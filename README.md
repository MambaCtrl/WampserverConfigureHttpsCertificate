# wampserver-configure-https-certificate
##记录wampserver配置https证书步骤
-------------------------------------------------------------------------------
下载项：  
1.WampServer --- 百度搜索然后官网下载  
2.OpenSSL --- https://slproweb.com/products/Win32OpenSSL.html  
注意：可以下载最新版，注意版本问题    

配置：  
1.打开cmd命令  
>输入apache的bin目录。--- D:\wamp\bin\apache\apache2.4.46\bin  

2.依次执行下列命令：    
  - openssl genrsa -aes256 -out private.key 2048  
  - openssl rsa -in private.key -out private.key  
  - openssl req -new -x509 -nodes -sha1 -key private.key -out certificate.crt -days 36500 -config D:\wamp\bin\apache\apache2.4.46\conf\openssl.cnf
  
  注意：执行命令期间，会让输入密码，或者国家地区一类的 ，按提示输入即可。  
     Common Name：localhost  

3.打开配置文件 D:\wamp\bin\apache\apache2.4.46\conf\extra\httpd-ssl.conf，在原来的配置中做如下修改：  
   - DocumentRoot "D:/wamp/www"  
   - ServerName localhost:443  
   - ServerAdmin admin@example.com  
   - ErrorLog "D:/wamp/bin/apache/apache2.4.46/logs/error.log" 
   - TransferLog "D:/wamp/bin/apache/apache2.4.46/logs/access.log"
   
   - SSLCertificateFile "D:/wamp/bin/apache/apache2.4.46/conf/key/certificate.crt"
   - SSLCertificateKeyFile "D:/wamp/bin/apache/apache2.4.46/conf/key/private.key"
   
   - CustomLog "D:/wamp/bin/apache/apache2.4.46/logs/ssl_request.log" \
          "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"
          
 4. 完成上述步骤后，在php.ini中药保证存在 extension=php_openssl.dll ，若没有extension=php_openssl.dll 那就添加这段，这段之前要是有“；”就先删除“；”再添加
 
 5.最后重启服务器，在浏览器输入 https://localhost:443  验证配置是否成功  
 OVER~
 
