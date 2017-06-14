# Redis积分中积分记录功能升级的过程

### 问题描述

当前用户操作（点赞、收藏、喜欢、评价、购买等）的积分记录都存储在Redis缓存中，再通过定时任务回写到数据库中。在开发2.5.3版本时，需求上要求能够统计出 积分操作的发起端属性（iOS、安卓）,所以需要在 原有的记录中增加设备属性字段。

考虑到数据结构变更，在不完全停止所有服务器的情况下，希望能够做到平滑切换，即允许部分服务器录入记录为新模型，部分录入记录为旧模型，同时切换过程中不丢失旧服务器产生的数据。

以下是现状及方案的考量和选择详情：

### 一、积分记录缓存升级前的状况

<center>![积分记录缓存示意图](http://photosd.nggirl.com.cn/work/9e43ffde64784fe48c304cb6de9c6aa1.png)
<div>积分记录缓存示意图</div>
</center>

1，Redis db1中存有两个列表接口，key分别是user_score_record_list和user_value_record_list，分别存放用户操作（评论、分享、点赞、收藏等等）获取和消耗的积分记录。

2，user_score_record_list列表中的元素，是类UserScoreRecord的实例，没有存放用户的设备信息的字段。user_value_record_list列表中，是UserValueRecord实例，同样也没有设备信息的字段。

3，数据库中user_score_record表和user_value_record表可没有设备信息字段，但可直接添加，添加字段对程序没有影响。

4，程序中存储用户积分缓存，有统一的入口，increaseUserScore直接调用即可将UserScoreRecord和UserValueRecord实例存入redis 的list。

5，nggirl项目和nggirl-web项目都可操作Redis，且都有添加记录用户的积分记录的功能（比如删除用户评论会扣除用户积分，需要写入redis，算作对应用户的积分记录）。所以修改后，两个项目需要同时更新。

6，nggirl项目有定时任务，每5分钟可将积分记录从Redis的list写入数据库。

### 二、解决方案一（未采用）

1，方案：直接使用Redis db1中原来定义的key（即user_score_record_list和user_value_record_list），代码中直接使用原有的model实例（即UserScoreRecord和UserValueRecord），直接修改实例、添加设备字段，直接修改原有的increaseUserScore记录设备信息。直接修改定时任务，将新实例写入数据库库。

2，会遇到的问题：在nggirl和nggirl-web部署过程中，用户操作产生的积分记录，依然会写入redis，这样同一个list中会同时存在两种model，且model的名字相同（包名类名都相同），在从redis反序列化成为Java实例时则会报错，无法获取model，用户的积分记录就会丢失。

3，解决方案：无，部分数据将会丢失。

### 三、解决方案二（已采用）

1，方案：在Redis db1中定义新的key、加入版本号（user_score_record_v253_list和user_value_record_v253_list），代码中使用新定义的model类型（UserScoreRecordV253和UserValueRecordV253），在新的类型中添加设备字段。添加新的increaseUserScore方法，组装新版的积分记录。添加新的定时任务实例，将新实例写入数据库。

2，会遇到的问题：在部署完两个项目（nggirl和nggirl-web）后需要触发一次原有的定时任务功能，将在部署期间写入redis的老版本内容（即user_score_record_list和user_value_record_list中的实例）转存到数据库。

3，解决方案：编写一个接口，手动触发原有的定时任务。


### 四、总结

使用方案二的好处是不会丢失数据，实现平滑过渡！
