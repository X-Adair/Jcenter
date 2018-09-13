# 项目上传jcenter配置

本项目是用于快速将想要开源的Android项目上传到jcenter。  
使用步凑如下：  

1. 在项目的build.gradle文件中添加以下插件：

```groovy
 classpath 'com.github.dcendents:android-maven-gradle-plugin:1.4.1'
 classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.7.1'
```

​	注:需要注意android-maven-gradle-plugin 插件与你使用的Gradle插件的版本关系，务必按照下表对应版本使用,否则会造成生成的Maven pom.xml文件没有第三方依赖。

| Plugin Version |            Plugin Name             |                 Dependency Information                 | Gradle Version |
| :------------: | :--------------------------------: | :----------------------------------------------------: | :------------: |
|      1.0       |           android-maven            |     com.github.dcendents:android-maven-plugin:1.0      |      1.8+      |
|      1.1       |           android-maven            |     com.github.dcendents:android-maven-plugin:1.1      |     1.12+      |
|      1.2       | com.github.dcendents.android-maven |     com.github.dcendents:android-maven-plugin:1.2      |      2.2+      |
|      1.3       | com.github.dcendents.android-maven |  com.github.dcendents:android-maven-gradle-plugin:1.3  |      2.4+      |
|     1.4.1      | com.github.dcendents.android-maven | com.github.dcendents:android-maven-gradle-plugin:1.4.1 |     2.14+      |
|      1.5       | com.github.dcendents.android-maven |  com.github.dcendents:android-maven-gradle-plugin:1.5  |      3.0+      |
|      2.0       | com.github.dcendents.android-maven |  com.github.dcendents:android-maven-gradle-plugin:2.0  |      4.1+      |
|      2.1       | com.github.dcendents.android-maven |  com.github.dcendents:android-maven-gradle-plugin:2.1  |      4.6+      |

2. 在module的build.gradle文件中加入以下代码：    

```groovy
apply from: "https://raw.githubusercontent.com/X-Adair/Jcenter/master/bintray.gradle"
```

3. 下载<a href="https://github.com/X-Adair/Jcenter/blob/master/project.properties">project.properties</a>文件放入需要开源的Module项目中，与build.gradle文件同级，并填写相关信息。 

4. 在local.properties中添加以下代码：

```
bintray.user=xxx     //xxx为你在bintray上的用户名
bintray.apikey=xxx   //xxx为bintray为你分配的api key   
```

​        <u>**请注意不要将local.properties文件上传到github，以防以上信息泄露。**</u>

5. 打开Android Studio的Terminal，执行以下命令：

```
./gradlew clean build
./gradlew bintrayUpload
```

​       如果以上两个命令都提示BUILD SUCCESSFUL，表示代码已经上传到bintray的仓库中

6. 进入bintray的项目中，点击Add to JCenter按钮，填写说明后进入审核，一般几小时后完成，然后就可以直接引用此项目。

