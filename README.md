# Systems Librarianship

Notes on sytems librarianship

Using this to show how to create a GitHub repo and to use Git on the commandline

more description

## Install a LAMP Stick

	**always check for updates**
	sudo apt update
	sudo apt -y upgrade

## Install Apache2

	create a webpage
	cd /var/www/html/
	sudo mv index.html index.html.original
	sudo nano index.html

## mysql

	sudo apt install mysql-server
	systemctl status mysql

	**root user**
	sudo su

	*becareful when using root user-can mess things up badly*

### Create a Bare Bones OPAC

	created a HTML form with code provided by Dr. Burns in his syslib book he is writing
	used his PHP search script BUT replaced IP addresss with my own
	connect to mysql
		my sql -u opacuser -p
	
	*use the information from login.php and use the opacdb to access the books table or modify*

	insert into books
	(author, title, publisher, copyright) values
	('Emma Donoghue', 'Room', 'Little, Brown \& Company', '2010-08-06'),
	('Zadie Smith', 'White Teeth', 'Hamish Hamilton', '2000-01-27');

#### Cataloging in the OPAC

	Create a page index.html and a php script (see Dr. Burns code)
	*make sure to change IP address to your own*
	
	use the php script to connect with mysql
	enter the books table within mysql database

	**security**
	you want only those with the correct user name and password to have access
	apache2.conf has to be overridden to change Allow Override None to Allow override all
	**see directions with Dr. Burns syslib book**

##### Install Wordpress

	**check requirements needed to install

	php --version
	mysql --version

	change to /var/www/html and use the commands
	
	sudo wget https://wordpress.org/latest.tar.gz
	sudo tar -xzvf latest.tar.gz

	switch to root linux user and log in as the mysql root user
	**be careful as root user**

	set up wp-conf.php
	add database name, user, password into wp-conf.php

	change the file ownership

	install wordpress
	detailed instructions at https://developer.wordpress.org/advanced-administration/before-install/howto-install/

	then customize your page



###### Install Omeka

	**check prerequisites**
	Install ImageMagick 
	
	sudo apt install imagemagick
	sudo a2enmod rewrite
	sudo systemctl restart apache2

	This is where I got stuck!!!
	install unzip 
	sudo apt install unzip

	retrieve Omeka Classic Zip file to extract
	cd/ var/www/html
	sudo wget https://github.com/omeka/Omeka/releases/download/v3.1/omeka-3.1.zip
	sudo unzip omeka-3.1.zip
	sudo cp -r omeka-3.1 omeka

	create a new user and a new database in mysql for omeka
	update db.ini file at /var/www/html/omeka

	change ownership sudo chown -R www-data:www-data *

	restart apache2 and mysql

	go to http://104.197.19.98/omeka/ to complete the installation

	customize the page

####### Install Koha

	Set up a new virtual machine with more RAM - check Koha prerequitisites
	
	check machine for updates 

	sudo apt autoremove -y && sudo apt clean

	install gnupg2
	sudo apt install gnupg2
	sudo reboot now

	Add Koha repository
	sudo su
	echo 'deb http://debian.koha-community.org/koha stable main' | sudo tee /etc/apt/sources.list.d/koha.list
	wget -q -O- https://debian.koha-community.org/koha/gpg.asc | sudo apt-key add -

	install koha
	apt update
	apt show koha-common
	apt install koha-common

	Configure Koha
	nano /etc/koha/koha-sites.conf
	change the line INTRAPORT="80" ro INTRAPORT="8080"

	apt install mysql-server
	set password:  mysqladmin -u root password bibliolib1

	a2enmod rewrite
	a2enmod cgi

	restart apache2

	create database
	koha-create --create-db bibliolib
	nano /etc/apache2/ports.conf 
	Listen 8080
	apachectl configtest
	systemctl restart apache2

	a2dissite 000-default
	a2enmod deflate
	a2ensite bibliolib
	systemctl reload apache2
	systemctl restart apache2
 

	Detailed instructions to install Koha at https://koha-community.org/manual//22.11/en/html/installation.html

	

 


