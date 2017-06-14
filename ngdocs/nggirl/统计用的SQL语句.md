# 有用的SQL语句
## 按照每日增加的新用户数进行统计

```sql
select regist, count(*),devicetype 
from (
  SELECT u.USERID,u.USERNAME,u.NICKNAME,ui.SEX,ui.DISTRICT,ui.ADDRESS,ui.BIRTHDAY,
  concat(date_format(ui.REGISTTIME,'%Y%m%d')) as regist, if(di.APPID='123456','苹果','安卓'
 ) as devicetype 
FROM pumpkincar.users u 
left outer join pumpkincar.userinfo ui 
on u.USERID=ui.USERID 
left outer join pumpkincar.user_deviceinfo di 
on u.USERID=di.USERID)as tempt  
group by tempt.regist order by tempt.regist
```

## 取得某个用户的个人信息

```sql
SELECT  u.USERNAME as 用户名,u.NICKNAME as 昵称,ui.DISTRICT as 区域,
 ui.ADDRESS as 地址,ui.PHONENUM as 电话,if(ui.SEX='1','女','男') as 性别 
FROM pumpkincar.users u 
left outer join pumpkincar.userinfo ui 
on u.USERID=ui.USERID 
where u.userid = 618;
```

##获取预约信息
```sql
SELECT r.RESERVATIONID as 预约编号, r.ADDRESS as 预约地址, r.WORKTYPE as 作品类型, 
 r.PRICE as 作品价格, r.CREATETIME as 下单时间,r.DATE as 约定日期, r.TIME as 约定时间, 
 d.REALNAME as 妆师姓名, u.NICKNAME 用户昵称, r.status 预约状态 
FROM pumpkincar.reservation r 
left outer join pumpkincar.users u 
on r.USERID=u.USERID 
left outer join pumpkincar.work w 
on r.WORKID=w.WORKID 
left outer join pumpkincar.dressers d 
on w.DRESSERID=d.USERID 
where d.AUTHENTICATION=1
order by CREATETIME desc;
```
 
##插入优惠券
```sql
insert into pumpkincar.user_coupon 
set USERID= 194, TITLE='南瓜券',STATUS=0,DEADLINE='永久有效',MONEY=30.00,BALANCE=30.00,
 GETTIME='2015-10-29 12:00:00',CODE='123546789',ISFOREVER=1,COUPONCODE='123456789'
```

##某个化妆师的全部作品插入到首单五折活动中

```sql
insert into pumpkincar.sale_channel_promotion_product(promotionid,productid)  
(select 2,workid FROM pumpkincar.work where dresserid in (SELECT userid FROM pumpkincar.dressers where REALNAME in ('蛋蛋','陈静','彭钰正杰','雷雨')) and deleted=0 
and WORKID not in (select productid from pumpkincar.sale_channel_promotion_product));
```

## 按照折后价格排序显示化妆作品列表
```sql
SELECT dresserid,realname,worktype,cost,if((select productid from pumpkincar.sale_promotion_products where productid=w.workid) is null,w.cost,w.cost/2) as price FROM pumpkincar.work w, pumpkincar.dressers d where w.deleted=0 and w.DRESSERID=d.USERID and d.REALNAME not like '%年会%' order by price
```

##获取所有用户的手机号
```sql
select distinct phone from  (select username as phone from pumpkincar.users where username like '1%'
union
select phonenum as phone from pumpkincar.userinfo where PHONENUM like '1%') as t limit 0,5000
```
> 备注：导出后需要清理掉10位长度的数字，去掉超过18xxxxxxxxx的数字。短信内容注意两点：1.如果在70个字左右，最好调整成70以内，短信发的量大，超过70字都是双倍的短信费用；2.在短信末尾添加"[T退订]"，短信前边！不用！加“【南瓜姑娘】”，系统会自动添加。

##获取账号类型
```sql
微博：SELECT userid, username,password FROM pumpkincar.users where username RLIKE '^[0-9]+$' and username not RLIKE '^PLUS' and password is null;

微信：SELECT userid, username,password FROM pumpkincar.users where username not RLIKE '^[0-9]+' and username not RLIKE '^PLUS' and password is null;

手机号：SELECT userid, username,password FROM pumpkincar.users where password is not null;
```

##妆品试用申请信息查询sql
```sql

SELECT userid as 用户编号, realname as 真实姓名, if(sex=0,'男','女') as 性别, age as 年龄, phonenum as 电话, wechat as 微信, skintype as 肤质,address as 地址, message as 留言 FROM pumpkincar.cosmetic_trial_apply_user where cosmeticid = 6
```
##mysqldiff对比数据库执行脚本
```bash
mysqldiff --server1=pumpkincar:Abcd123456789@rdszwx0xrng2p55cll50.mysql.rds.aliyuncs.com --server2=root:Abcd123456789@testcli1.nggirl.com.cn pumpkincar:pumpkincar --force >d:/dblog.txt
```
