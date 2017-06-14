# Xss攻击及防御
先说两个题外话：
安全防护可以考虑的方面：操作系统（服务器）-密码破解/ddos/cc、数据传输-https/认证机制、业务逻辑（验证操作数据和所有人关系）、前端（认证信息或者挂马）-xss

被XSS攻击对南瓜姑娘可能会带来的影响：当前h5站采用的是和app相同的认证机制，即授权令牌机制，那么：1方面攻击者可以通过嵌入代码，获取用户的授权令牌，后续进行恶意操作；第2方面，攻击者可以直接嵌入恶意代码，造成所有的访问用户，均称为攻击者的攻击工具。或者攻击南瓜姑娘，或者利用南瓜姑娘的访问用户攻击其他网站（可能性不大，因为攻击者不能稳定的控制攻击流量）。
##关于xss
[XSS百度百科](http://baike.baidu.com/link?url=bk_aPkkAoFPaKqIPbf_Q10z0-gCzHeWuFzbEm86CzbwlMUlDFrXfNtFYQUyfhnoPZX0MzZbYQvay1deJUeUiX_)
[防御XSS的七条原则](http://www.oschina.net/news/43919/7-principles-of-defense-xss)
##前端防御方法
http://lobert.iteye.com/blog/2164741

##后端防御方法
http://blog.csdn.net/happylee6688/article/details/40660797

##当前架构下，后端防御Xss实现
实现的思路是过滤输入字符串，但是可实现的位置有3个：1.Filter、2.Interceptor、3.Aspect。

Filter方式需要实现一个HttpServletRequestWrapper类，来对request请求进行包装。即上一节后端防御中说道的方式。但是，实质上，上述方式仅仅考虑到了get请求，对于post请求的参数是在request的stream中的，需要单独提取，而不能用getParameter获取到。所以，在实现上需要二外处理post类型请求。这里有一个风险就是，会不会影响到spring对multipart类型数据的解析？所以技术难度相对较大。

Interceptor方式中也可以多request进行处理，然后将request包装到自定义的HttpServletRequestWrapper中。为什么这里可以去简单包装？因为这里的request是spring处理之后的request，已经把所有的post参数调整到了getParameter中。但是，由于Interceptor不像Filter是一个链式传递的架构，所以就算封装成功，但是不能顺利的传递给Interceptor代理的真是方法中。

所以，我们只剩下Aspect一种方式。

也就是请求到达tomcat之后的处理过程是：EncodingFilter-->OtherFilter-->dispatchServlet-->OurAspect-->interceptor--->controller-->service-->dao

XssAdvice.java实现：

```java
package com.pumpkin.carriage.interceptor;

import java.lang.reflect.Field;

import org.aspectj.lang.ProceedingJoinPoint;

public class XssAdvice {
    private Object doAround(ProceedingJoinPoint pjp) throws Throwable {  
        System.out.println("-----doAround().invoke-----");  
        System.out.println(" 此处可以做类似于Before Advice的事情");  
        Object[] args = pjp.getArgs();
        for(int i= 0; i< args.length; i++){
        	if(args[i] == null){
        		continue;
        	}
        	
        	if(args[i] instanceof String){
            	args[i] = cleanXSS((String)args[i]);
            }
        	
        	Field[] fields = args[i].getClass().getDeclaredFields();
        	for(Field field : fields){
        		try{
        			Object obj = field.get(args[i]);
        			if(obj instanceof String){
        				obj = cleanXSS((String)obj);
        				field.set(args[i], obj);
        			}
        		}catch(Exception e){
        			//
        		}
        	}
        }
        
        //调用核心逻辑  
        Object retVal = pjp.proceed(args);  
          
        System.out.println(" 此处可以做类似于After Advice的事情");  
        System.out.println("-----End of doAround()------");  
        return retVal;  
    }  
    
    private String cleanXSS(String value) {  
        value = value.replaceAll("<", "& lt;").replaceAll(">", "& gt;");  
        value = value.replaceAll("\\(", "& #40;").replaceAll("\\)", "& #41;");  
        value = value.replaceAll("'", "& #39;");  
        value = value.replaceAll("eval\\((.*)\\)", "");  
        value = value.replaceAll("[\\\"\\\'][\\s]*javascript:(.*)[\\\"\\\']", "\"\"");  
        value = value.replaceAll("script", "");  
        return value;  
    } 
}

```

xml方式配置aop切面(放到spring-mvc的配置文件中)：

```xml
 	    <bean id="xssAdvice" class="com.pumpkin.carriage.interceptor.XssAdvice" />  
    <aop:config>  
        <aop:aspect id="aspect" ref="xssAdvice">  
            <aop:pointcut id="controllMethods" expression="execution(* com.pumpkin.carriage.controller..*.*(..))"/>  
            <!-- <aop:pointcut id="controllMethods" expression="execution(* com.pumpkin.carriage.controller.*Controller.*(..))"/>   -->
              
            <aop:around method="doAround"  pointcut-ref="controllMethods"/>  
              
        </aop:aspect>  
    </aop:config> 
```
