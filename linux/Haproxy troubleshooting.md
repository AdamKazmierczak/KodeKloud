xFusionCorp Industries has an application running on Nautlitus infrastructure in Stratos Datacenter. The monitoring tool recognised that there is an issue with the haproxy service on LBR server. That needs to fixed to make the application work properly.

Troubleshoot and fix the issue, and make sure haproxy service is running on Nautilus LBR server.

Click on ✔ and Do Task Again
#check the systemctl service 
#ssl to haproxy loadbalancer

systemctl status haproxy 

#it looks like there is something wrong within cfg file. 

Check the configuration of the file by running in the haproxy folder 
haproxy -c -f -haproxy.cfg

Proxy 'main': unable to find required default_backend: 'app'.

#vi the file haproxy cf. It looks like backend app is commented.
#remove the comment and run again 

###
backend app  #it should look like this 
###
check if the haproxy.cfg is ok by running 

haproxy -c -f -haproxy.cfg

#then run 

systemctl start haproxy
system status haproxy
