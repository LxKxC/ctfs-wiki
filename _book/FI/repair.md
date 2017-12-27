# 漏洞修复
####代码层,包含的参数设置为白名单。
```
<?php  
 $filename = $_GET['filename'];  
 switch ($filename) {  
 case 'index':  
 case 'home':  
 case 'admin':  
 include '/var/www/html/' .$filename .'.php';
 break;    
 default:  
 include '/var/www/html/' .$filename .'.php'; 
}  
?>  
```
####web服务器配置

修改php的配置文件将open_basedir的值设置为可以包含的特定目录，后面要加/，例如：open_basedir=/var/www/html/

关闭allow_url_fopen可以防止本地文件包含和远程文件包含

关闭allow_url_include可以防止远程文件包含