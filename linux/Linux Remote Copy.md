One of the Nautilus developers has copied confidential data on the jump host in Stratos DC. That data must be copied to one of the app servers. Because developers do not have access to app servers, they asked the system admins team to accomplish the task for them.
Copy /tmp/nautilus.txt.gpg file from jump server to App Server 2 at location /home/opt.

Click on ✔ and Do Task Again
#copy file to home folder of steve
scp nautilus.txt.gpg steve@stapp02:/home/steve

#ssh to app server 002 
ssh steve@stapp02

#move file from home folder of steve to /home/opt/ via command mv 
#you need to do this as sudo  and input steve password

sudo mv nautilus.txt.gpg /home/opt
