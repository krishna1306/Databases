### Install MySQL

```bash
wget https://dev.mysql.com/get/mysql180-community-release-el7-3.noarch.rpm

rpm -ivh mysql180-community-release-el7-3.noarch.rpm

yum install mysql-server

service mysqld start

service mysqld status
```

### Install MySQL using only `yum`

```bash
sudo yum install https://dev.mysql.com/get/mysql57-community-release-el7-9.noarch.rpm

sudo yum install mysql-community-server
```

**Always refer to documentation when installing in production environment**

Default port `3306`

```
/var/log/mysqld.log
```

When the database is installed, it generates a temp password - which can be seen in **this log**

**Default data directory** is `/var/lib/mysql`

**Connect to the database**

```
mysql -u root -p<password>
```

Note that there is **no space** after the `-p` flag

---

#### Change the default `root` password before proceeding

```mysql
ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPass4!'

#or

SET PASSWORD = PASSWORD('P@ssw0rd123');
FLUSH PRIVILEGES;
```

#### Or - run the below shell script which does it for you

```
mysql_secure_installation
```

#### Create User

```mysql
CREATE USER 'john'@'localhost' IDENTIFIED BY 'MyNewPass4!'
```

**Better to use unprivileged users** for accessing the database

You can also mention the IP in the place of `localhost` 

Use `%` in the place of `localhost `-- similar to using `0.0.0.0` 

#### Managing Privileges (Authorisation)

```mysql
GRANT <PERMISSION> ON <DB.TABLE> TO 'john'@'%'
GRANT SELECT, UPDATE ON school.* TO 'john'@'%'

SHOW GRANTS FOR 'john'@'localhost';
```

**PERMISSIONS available**

- ALL PRIVILEGES

- CREATE

- DROP

- DELETE

- INSERT

- SELECT

- UPDATE

---

```mysql
SHOW DATABASES;

CREATE DATABASE school;

USE school;

CREATE TABLE persons;

SHOW TABLES;

INSERT INTO persons values ("John Doe", 45, "new york");

SELECT * FROM persons;
```

