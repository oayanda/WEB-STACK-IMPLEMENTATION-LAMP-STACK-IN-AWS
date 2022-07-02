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

![apt update](./images/10.png)

`sudo apt install apache2`

![install apache2`](./images/11.png)


2. **Verify Apache2 service is running.**

`sudo systemctl status apache2`

![Apache2 running](./images/12.png)

2. **Now access the installed apache2 server locally .**

` curl http://127.0.0.1:80`

![Apache2 running locally](./images/13.png)

3. **Confirm the Apache2 server is accesiable in the browser. - Make sure the security group allows both tcp and ssh remote connection**

` http://52.73.55.62:80` - in the browser or 

`curl -s http://52.73.55.62:80` - via the remote connection

![Apache2 running locally](./images/14.png)


####  Step Three - Time to install the MySql database  on the Apache server.
1. ** install MySql Server package** 

`sudo apt install mysql-server`

![MySql server](./images/15.png)

2. **Log into the install MySql console.**

`sudo mysql`

![Login in Mysql Console](./images/16.png)

2. **Aasign a password *PassWord.1* to Admin User ROOT and exit.**

`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`

![Password](./images/17.png) 

2. **Start an interactive script. - The process allows default logins and database to be removed for better security**

`sudo mysql_secure_installation`

![Password](./images/18.png) 

####  Step Four - Time to install Php.
1. **Three PHP packages would be require** 
- Php package
- php-mysql package - communication with MySql
- libapache2-mod-php - php communication with Apache2 server

`sudo apt install php php-mysql libapache2-mod-php`

![MySql server](./images/20.png)

####  All LAMP Components are now up and runnning.

 #### **Step Five -** Test the setup - Configure a Apache Virtual Host to host our web application which would serve client computers.

 1. Create a domain "projectlamp" under the /www directory and assign ownership to your currect system user

`sudo mkdir /var/www/projectlamp`

`sudo chown -R $USER:$USER /var/www/projectlamp`

 ![MySql server](./images/01.png)

  2. Create a configure file in Apaches's sites-available directory

`sudo vi /etc/apache2/sites-available/projectlamp.conf`


 ![MySql server](./images/02.png)

 3. Show the new projectlamp.conf file

`sudo ls /etc/apache2/sites-available`


 ![MySql server](./images/03.png)
 4. Enable the new virtual host, 

- `sudo a2ensite projectlamp`
- Disable default Apache's default website

- `sudo a2dissite 000-default`

- Finally, reload Apache

- `sudo apache2ctl configtest`

 ![MySql server](./images/04.png)

5. The new directory is empty - Let's create an index.html file
- Make sure to change the ip to your external IP

`sudo echo 'Hello LAMP from hostname' $(curl -s "52.87.225.72"/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://52.87.225.72/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`

![MySql server](./images/05.png)

5. Now let's view our website in the browser
- View with Public Ip
- `http://52.87.225.72:80`
![MySql server](./images/06.png)

- view with Public DNS
![MySql server](./images/07.png)