# wampserver-configure-https-certificate
-----------------------------------------
#记录wampserver配置https证书步骤
-------------------------------------------------------------------------------
##下载项：  
1.WampServer --- 百度搜索然后官网下载  
2.OpenSSL --- https://slproweb.com/products/Win32OpenSSL.html  
注意：可以下载最新版，注意版本问题  
-------------------------------------------------------------------------------
配置：  
1.打开cmd命令  
  输入apache的bin目录。--- D:\wamp\bin\apache\apache2.4.46\bin  
2.依次执行下列命令  
  - openssl genrsa -aes256 -out private.key 2048  
  - openssl rsa -in private.key -out private.key  
  - openssl req -new -x509 -nodes -sha1 -key private.key -out certificate.crt -days 36500 -config D:\wamp\bin\apache\apache2.4.46\conf\openssl.cnf  
 
