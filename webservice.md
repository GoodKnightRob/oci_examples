# Steps to create a static webservice on Oracle Linux


```
 sudo yum install httpd -y
 sudo apachectl start
 sudo systemctl enable httpd
 sudo apachectl configtest
 sudo firewall-cmd --permanent --zone=public --add-service=http
 sudo firewall-cmd --reload
 sudo bash -c 'echo This is an app server 1 >> /var/www/html/index.html'
  ```
  
  You can then edit the index.html with whatever html content you'd like to serve
  ```
  sudo chmod +w index.html 
  vi index.html 
  ```
  
   
