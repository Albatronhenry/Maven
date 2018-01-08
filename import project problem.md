### ArtifactTransferException: 

Failure to transfer org.springframework:spring-aop:jar:3.2.8.RELEASE from http://repo.maven.apache.org/maven2 was cached in the local repository...

意思是：

对于这个包传输以本地仓库失败，解决不会重新试，直到maven再改更新索引，或强制更新。

-----------------

解决办法是：直接去本地仓库，(D:\SoftWareCustomer\Maven\maven_repository\repository\)
把这个spring-aop:jar:3.2.8.RELEASE 的目录删除掉（因为包没有下载下来），再次刷新你的项目就中以了，或者在你的项目上右击，选择maven—>update project就可以了
