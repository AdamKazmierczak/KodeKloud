Task Details
A developer Jim has been assigned Nautilus project temporarily as a backup resource. As a temporary resource for this project, we need a temporary user for Jim. It’s a good idea to create a user with a set expiration date so that the user won't be able to access servers beyond that point.


Therefore, create a user named jim on the App Server 3. Set expiry date to 2021-03-28 in Stratos Datacenter. Make sure the user is created as per standard and is in lowercase.

Click on ✔ and Do Task Again
ssh to app server 3 as banner

ssh banner@stapp03 
#input password from 
https://kodekloudhub.github.io/kodekloud-engineer/docs/projects/nautilus

#then run command as sudo with expiry date such as 
#example run sudo useradd -e year-month-day username

sudo useradd -e 2021-03-28 jim
