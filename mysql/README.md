# MySql Docker Container

Run these commands from within the mysql folder.

1. Build the image
`docker build -t mysql .`

2. Start the container
`docker run -p 3306:3306 --name mysql -d mysql`

You can check its running by `docker ps`

3. execute command within
`docker exec -it mysql bash`

Type `mysql` to access the database.

**Notes**
To access this properly you will need to create a separate user and adjust MySql configuration so that the bind address is  0.0.0.0.

To add the user, type

`mysql`

`CREATE USER 'developer'@'%' IDENTIFIED BY 'password';`

`GRANT ALL PRIVILEGES ON *.* TO 'developer'@'%';`

To change the bind address we will install the nano text editor.

`apt-get install nano`

`nano /etc/mysql/mysql.conf.d/mysqld.cnf`

change the bind address to 0.0.0.0 then hit ctrl-x to save

Exit the container by typing `exit` and reboot the container by typing `docker reboot mysql`
