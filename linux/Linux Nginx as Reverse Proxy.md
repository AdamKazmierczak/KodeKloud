#login to stbkp01
ssh clint@stbkp01

#install httpd
yum install httpd
#install repo for nginx
yum install epel-release
#install nginx 
yum install nginx

#go to httpd.conf and edit 
sudo  vi  /etc/httpd/conf/httpd.conf

#update listen to port specific for Apache
Listen 6000

#Go to server name and add uncoment 
172.16.238.16:6000

#Go to nginx config by typing

vi /etc/nginx/nginx.conf

#and input where 8095 is nginx port being used for redirection to apache. And proxy pass is for apache port in this example 6000
#to the 
server {
 listen       8095 default_server;
 listen       [::}:8095 default_server;
 server_name  172.16.238.16;
 root         /usr/bin/share/nginx/html;
 
 ....
 
 location / {
    proxy_pass http://172.16.238.16:6000
 }
 
 
 #then go to jump server on another terminal or so.
 sudo scp /home/index.html clitn@stbkp01:tmp
 
 #and swith to terminal of backup server
 
 cp /tmp/index.html /var/www/html
 
#as checkup from jump server port of nginx server 
curl http://172.16.238.16:8095

#and you should see output from index file.
