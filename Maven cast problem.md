# Maven

Maven project's problem
<scope>，它主要管理依赖的部署。目前<scope>可以使用5个值：  
1. compile，默认值，会随着项目一起发布。 
2. provided，类似compile，希望运行容器提供。 
3. runtime，运行时使用。 
4. test，只在测试时使用,不会用于发布。 
5. system，类似provided


* Q:
java.lang.ClassCastException: com.yonyou.TestServlet cannot be cast to javax.servlet.Servlet

* A:
servlet-api.jar与tomcat自带的包冲突，需要加上scope

```xml
 <dependency>
     <groupId>javax.servlet</groupId>
     <artifactId>servlet-api</artifactId>
     <version>2.5</version>
     
     
     
                              <scope>provided</scope>  <!--作用域加上即可-->
     
     
</dependency>
```
