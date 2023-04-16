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
