####  Step One - Spin up a AWS instance - This is the virtual hardware on which LAMP would be implemented.
1. **Login into your AWS** 
2. **Lunch your Ec2 instance type.**
![EC2 instance](./images/1.png)
3. **One instance is good enough and selected**
![EC2 instance](./images/2.png)
4. **Use the default settings.**
![EC2 instance](./images/3.png)
5. **Configure Security Group, generate a key pair and lunch.**
![EC2 instance](./images/5.png)
6. **ssh into aws from windows terminal.**
![EC2 instance](./images/6.png)

####  Step Two - Installing Apache and updating the firewall
1. **Use the apt command - update all packages and install apache2 package** 

`sudo apt update`
![apt update](./images/11.png)
`sudo apt install apache2`
![install apache2`](./images/11.png)


2. **Verify Apache2 service is running.**

`sudo systemctl status apache2`
![Apache2 running](./images/12.png)

2. **Now access the installed apache2 server locally .**

` curl http://127.0.0.1:80`
![Apache2 running locally](./images/13.png)

3. **Confirm the Apache2 server is accesiable in the browser. - Make sure the security group allows but tcp and ssh remote connection**

` http://52.73.55.62:80` - in the browser or 

`curl -s http://52.73.55.62:80` - via the remote connection
![Apache2 running locally](./images/14.png)


####  Step Three - Time to install the MySql database  on the Apache server.
1. **Use the apt command - update all packages and install apache2 package** 

`sudo apt install mysql-server`
![MySql server](./images/15.png)

2. **Log into the install MqSql console.**

`sudo mysql`
![Login in Mysql Console](./images/16.png)
