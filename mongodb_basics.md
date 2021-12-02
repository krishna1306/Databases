### Install MongoDB

Document ---> Collection ---> Database ---> MongoDB Server

1. Add `mongodb` repo to `yum`

   1. ```
      vim /etc/yum.repos.d/mongodb-org-5.0.repo
      ```

   2. ```
      [mongodb-org-5.0]
      name=MongoDB Repository
      baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/5.0/x86_64/
      gpgcheck=1
      enabled=1
      gpgkey=https://www.mongodb.org/static/pgp/server-5.0.asc
      ```

2. ```bash
   yum install mongodb-org
   ```

### Check

```
systemctl start mongod
systemctl status mongod
```

Logs are at `/var/log/mongodb/mongod.log`

Default port is `27017`

These settings can be changed at `/etc/mongod.conf` along with

- IP address on which port should be listening
- DB Storage file and path
- Log path etc.,

### Connect

```
mongo
```

*By default, access control is not enabled*

```mongo
# Show all DBs
show dbs

# Create and switch to database
use school

# See the current db
db

# Create collection
db.createCollection("persons")

# See all collections in a db
show collections

# Insert a new document
db.persons.insert({
	"name" : "John Doe",
	"age" : 45,
	"location" : "New York",
	"salary" : 5000
})

# Find records
db.persons.find()
db.persons.find({"name": "John Doe"})
```

**Mongo Syntax will follow JavaScript**

