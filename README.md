# 项目上传jcenter配置

本项目是用于快速将想要开源的Android项目上传到jcenter。  
使用步凑如下：  
* 1.在项目的build.gradle文件中添加以下插件：
    <pre>
      <code>
        classpath 'com.github.dcendents:android-maven-gradle-plugin:1.4.1'
        classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.7.1'
      </code>
    </pre>
* 2.在module的build.gradle中加入以下代码：    
    <pre>
      <code>
        apply from: "https://raw.githubusercontent.com/X-Adair/Jcenter/master/bintray.gradle"
      </code>
    </pre>  
* 3.下载<a href="https://github.com/X-Adair/Jcenter/blob/master/project.properties">project.properties</a>文件放入需要开源的Module项目中，与build.gradle文件同级，并填写相关信息。 
* 4.在local.properties中添加以下代码：

    <pre>
      <code>
         bintray.user=xxx     //xxx为你在bintray上的用户名
         bintray.apikey=xxx   //xxx为bintray为你分配的api key    
      </code>
    </pre>
    请注意不要将local.properties文件上传到github，以防以上信息泄露。
* 5.打开Android Studio的Terminal，执行以下命令：
    <pre>
      <code>
        ./gradlew clean build
        ./gradlew bintrayUpload
      </code>
    </pre>
    如果以上两个命令都提示BUILD SUCCESSFUL，表示代码已经上传到bintray的仓库中
* 6.进入bintray的项目中，点击Add to JCenter按钮，填写说明后进入审核，一般几小时后完成，然后就可以直接引用此项目。
    
