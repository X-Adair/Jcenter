# 项目上传jcenter配置

本项目是用于快速将想要开源的Android项目上传到jcenter。  
使用步凑如下：  
* 1.下载project.properties文件放入项目中，与local.properties文件目录同级，并填写相关信息  
* 2.在local.properties中添加以下代码   
    <pre>
        <code>
            bintray.user=xxx     //xxx为你在bintray上的用户名
            bintray.apikey=xxx   //xxx为bintray为你分配的api key
        </code>
    </pre>
    请注意不要将local.properties文件上传到github，以防以上信息泄露。    