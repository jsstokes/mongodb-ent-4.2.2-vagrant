# mongodb-ent-4.2.2-vagrant
MongoDB Enterprise 4.2.2 on Ubuntu Server 18.04.3 LTS

By default, these files will deploy MongoDB Enterprise v4.2.x.
If you want to install a different version, simply set the environment variable `"MONGO_VERSION"` to either "4.0" or "4.2".

For example:

`export MONGO_VERSION=4.0`

or 

`export MONGO_VERSION=4.2`

**Note:** *Any other value **will** cause the provisioning step to fail*

## Usage
1. Use git to clone this repository
1. run `vagrant up` in the newly cloned directory 
1. Once complete, `vagrant ssh` will give you an ssh connection into the VM. 

## Testing
Once inside the ssh shell, the command `mongo` should produce something like:
```
vagrant@mongo40:~$ mongo
MongoDB shell version v4.2.2
connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("b5b62a8a-c465-4383-add7-689a09dce271") }
MongoDB server version: 4.2.2
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see
	http://docs.mongodb.org/
Questions? Try the support group
	http://groups.google.com/group/mongodb-user
Server has startup warnings:
2020-01-24T03:47:54.237+0000 I  STORAGE  [initandlisten]
2020-01-24T03:47:54.237+0000 I  STORAGE  [initandlisten] ** WARNING: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine
2020-01-24T03:47:54.237+0000 I  STORAGE  [initandlisten] **          See http://dochub.mongodb.org/core/prodnotes-filesystem
2020-01-24T03:47:54.919+0000 I  CONTROL  [initandlisten]
2020-01-24T03:47:54.919+0000 I  CONTROL  [initandlisten] ** WARNING: Access control is not enabled for the database.
2020-01-24T03:47:54.919+0000 I  CONTROL  [initandlisten] **          Read and write access to data and configuration is unrestricted.
2020-01-24T03:47:54.919+0000 I  CONTROL  [initandlisten]
MongoDB Enterprise >
```

## Restarting mongod
If you shutdown the VM, the mongod process will have to be restarted with `sudo service mongod start`
