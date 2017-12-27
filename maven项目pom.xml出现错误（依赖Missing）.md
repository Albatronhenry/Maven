# [Maven 项目pom.xml出现错误（依赖Missing）](http://www.cnblogs.com/1314wamm/p/7235453.html)

Maven的依赖问题
在聚合模块时候，发现在父工程目录中的依赖存在一些问题。一开始是${pagehelper.version} 

依赖添加失败
* 在父工程的jar包依赖在子工程中无法进行添加报错*

```xml
 <pagehelper.version> 3.4.2-fix </pagehelper.version>
 
 ```
 
` Missing artifact com.github.pagehelper:pagehelper:jar:3.4.2-fix ` 

原因
在父工程中已经确定jar的version，但是jar下载不下来，可能存在两种情况 

---------

1. 该jar包非免费，需要付费，所以下载不下来 
2. 网络原因，连接不到国外的服务器

---------
所以在父类中改成了低版本(3.2.1)，

```xml

 <pagehelper.version>3.2.1</pagehelper.version>


      <dependency>
				<groupId>com.github.pagehelper</groupId>
				<artifactId>pagehelper</artifactId>
				<version>${pagehelper.version}</version>
			</dependency>

 
```
然后

![自启动](https://github.com/Albatronhenry/UploadFile/blob/master/pic/maven%E5%90%AF%E5%8A%A8%E8%87%AA%E6%9B%B4%E6%96%B0%E9%A1%B9%E7%9B%AE.png)

 

 最后run as-->maven install即可
