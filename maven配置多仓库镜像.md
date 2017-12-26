###  [maven配置多仓库镜像](http://blog.csdn.net/haohaizijhz/article/details/72841489)

* 问题描述：相应jar包从中央仓库下载老式显示连接超时，pom文件报错

    Failure to transfer com.fasterxml.jackson.core:jackson-core:jar:2.4.2 from https://repo.maven.apache.org/maven2 was cached in the local 
repository, resolution will not be reattempted until the update interval of central has elapsed or updates are forced. Original error: 
Could not transfer artifact com.fasterxml.jackson.core:jackson-core:jar:2.4.2 from/to central (https://repo.maven.apache.org/maven2): 
connect timed out

-----------------------

用阿里的镜像替代远程中央镜像

大部分jar包都可以在阿里镜像中找到，部分jar包在阿里镜像中没有，需要单独配置镜像

我所处的阶段：
修改了maven的全局配置文件setting.xml(其所处位置maven的安装目录maven/apache-maven-3.3.9/conf/setting.xml)：
1、配置了本地仓库：

```xml

<localRepository>D:\SoftWareCustomer\Maven\maven_repository\repository</localRepository>

```
2、配置了中央仓库的镜像：（换成了阿里的）
```xml

<mirror>      
  <id>nexus-aliyun</id>    
  <name>nexus-aliyun</name>  
  <url>http://maven.aliyun.com/nexus/content/groups/public</url>    
  <mirrorOf>central</mirrorOf>      
</mirror>  

```
希望你也做到了这一步。并且知道了mirrorOf为什么要配置为central


最后记得在相应项目右击--maven-- update project
[](https://github.com/Albatronhenry/UploadFile/blob/master/pic/%E6%9B%B4%E6%96%B0maven%E9%A1%B9%E7%9B%AE.png)
