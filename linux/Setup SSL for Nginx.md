The system admins team of xFusionCorp Industries needs to deploy a new application on App Server 1 in Stratos Datacenter. 
They have some pre-requites to get ready that server for application deployment. Prepare the server as per requirements shared below:
Install and configure nginx on App Server 1.
On App Server 1 there is a self signed SSL certificate and key present at location /tmp/nautilus.crt and /tmp/nautilus.key. Move them to some appropriate location and deploy the same in Nginx.
Create an index.html file with content Welcome! under Nginx document root.
For final testing try to access the App Server 1 link (either hostname or IP) from jump host using curl command. For example curl -Ik https://<app-server-ip>/.


Click on ✔ and Do Task Again
--add nginx reposity

install ngingx repository
sudo yum install epel-release -y

install nginx
sudo yum install nginx -y

sudo su

--copy cert files to folders from tmp to /etc/pki/CA/certs and /etc/pki/CA/certs/private
cp tmp/nautilus.crt /etc/pki/CA/certs/nautilus.crt
cp tmp/nautilus.key /etc/pki/CA/private/nautilusk.key 

--check if keys have been copied

--go to the folder /etc/nginx/
cd /etc/nginx

--edit nginx.conf file 
sudo vi nginx.conf

--search for and change server name to stapp01 ip. Uncoment section regarding Server { listen 443 ...}. Add ip to server name in section 443

server {
     listen 80
     ....
}

server {
   listen 443 ssl 
   ....
}


--restart nginx service

sudo systemctl restart nginx
--if nginx do not start up you have error in config file nginx.conf

--change schell to tony / normal user

go to folder /usr/share/nginx/html and create file index.html with Welcome! text
sudo vi /usr/share/nginx/html/index.html

--check if there are proper rights on file 
ls /usr/share/nginx/html/index.html -all

if not then add those via 
sudo chmod +x index.html

go to jump server and check if everything works as should
curl -Ik https://ip_adress_of_app_sever

