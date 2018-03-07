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


[参考方案2](http://roufid.com/no-compiler-is-provided-in-this-environment/)

Problem

You may face the below Maven error while running a Maven build :

No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK?

Solution

Your JAVA_HOME environment variable or your Eclipse IDE are pointing to a JRE rather than a JDK. You must set a correct compiler in your environment and below 3 ways to perform it:

Refer the JAVA_HOME to a JDK

Maven on Eclipse : The correct configuration

Fix the problem in the pom.xml

### 1- Refer the JAVA_HOME to a JDK

If you are running Maven on command line, it is very likely that your Maven environment is not configured correctly. In fact, Maven relies on the JAVA_HOME environment variable to use the right compiler. JAVA_HOME must refer to a JDK (JAVA Development Kit) and not a JRE (Java Runtime Environment). See the difference between a JDK and a JRE

To check what your Maven uses, open a command line and type:


mvn –version

Output:

![java-home](https://github.com/Albatronhenry/UploadFile/blob/master/pic/java_home.png)

Verify that JAVA_HOME refers to a JDK home and not a JRE. It refers to a JRE in the previous example.

Below how to update the value of JAVA_HOME:

On Windows:

Go to System properties -> Advanced system settings -> Advanced -> environment variable and on the System variables section select the JAVA_HOME variable and click on Edit

Fill the form with the following

Variable name: JAVA_HOME

Variable value: <ABSOLUTE_PATH_TO_JDK_HOME>

![1-java-home](https://github.com/Albatronhenry/UploadFile/blob/master/pic/1_java_home.png)

If you are using command line you can set the variable before running the build as following:

```xml

set JAVA_HOME=<ABSOLUTE_PATH_TO_JDK>

```

On Unix:

```xml

export JAVA_HOME=”<ABSOLUTE_PATH_TO_JDK>”

```

### 2- Running Maven in Eclipse

If you are running Maven from your IDE you must check that your environment is using a JDK rather than a JRE. Below how to perform the check:

Open your Eclipse, click on Windows -> Preferences -> Java -> Installed JREs

Verify that the checked JRE refers to a JDK : Select the checked JRE and click Edit… and change the path to the JDK home.

![jdk-perference](https://github.com/Albatronhenry/UploadFile/blob/master/pic/jdk-Preferences.png)

* Click OK.

The “No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK?” Maven error will disappear.

### 3- Adding the configuration in the pom.xml

Another solution is to fork the maven-compiler-plugin and set the full path to the correct Java compiler as blow :

```xml

<project ...>
	...
	<build>
		...
		<plugins>
			<plugin>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.1</version>
				<configuration>
					<source>1.7</source>
					<target>1.7</target>
					<fork>true</fork>
					<executable>C:\Program Files\Java\jdk1.7.0_79\bin\javac</executable>
				</configuration>
			</plugin>
		</plugins>
	</build>
	...
</project>

```
