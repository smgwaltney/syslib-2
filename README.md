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
