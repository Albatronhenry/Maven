### [No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK?](http://blog.csdn.net/testcs_dn/article/details/42975411)

ERROR MESSAGE:

```

[INFO] -------------------------------------------------------------  
[ERROR] No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK?  
[INFO] 1 error  
[INFO] -------------------------------------------------------------  
[INFO] ------------------------------------------------------------------------  
[INFO] BUILD FAILURE  
[INFO] ------------------------------------------------------------------------  

```

solve method:
  excute step：
  
-----------

  Maven update
  
![m-u](https://github.com/Albatronhenry/UploadFile/blob/master/pic/update%20project.png)

  Maven clean
  
  ![m-c](https://github.com/Albatronhenry/UploadFile/blob/master/pic/maven-clean-install.png)

  project clean
  
  build project
  
  ![p-b](https://github.com/Albatronhenry/UploadFile/blob/master/pic/project.png)
  
------------

然后再重复的执行Maven Install，直到打包成功为止。
