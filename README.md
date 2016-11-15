#Steps for transfer Magento from live server to localhost on Windows

1. Copy all files and folders from public_html to for example: D:/Projects/www/magento-demo
2. Delete all files from D:/Projects/www/magento-demo/var/cache
3. Export database from remote
4. Import database to local
5. Change 'web/unsecure/base_url' and 'web/secure/base_url' in 'core_config_data' table 
6. Change connection to DB (host, user, password, database) in D:/Projects/www/magento-demo/app/etc/local.xml

#Create vhost
7. In C:\Windows\System32\drivers\etc\hosts add line:
   127.0.0.1 		magento-demo.local
   
8. Find and uncomment (remove #) lines in httpd.conf:
  LoadModule vhost_alias_module modules/mod_vhost_alias.so
  Include conf/extra/httpd-vhosts.conf

9. Add code in conf/extra/httpd-vhosts.conf:
  <VirtualHost *:80>
    ServerName magento-demo.local
    DocumentRoot "D:\Projects\www\magento-demo"
    <Directory "D:\Projects\www\magento-demo">
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>

10. Restart Apache

11. Open url 'magento-demo.local' in browser
 
  
