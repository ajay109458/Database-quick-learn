# MongoDB commands

## Quick commands
* **help** - show help 
* **show dbs** – print all databases on the server
* **use &lt;db&gt;** - switch current database to &lt;db&gt;
* **show collections** - print out all the collections in the current database. 
* **show users** – print list of all users in the current databse. 
* **show roles** – print list of all the roles, user-defined and built-in for the current database. 
* **show profile** – print five more recent operation that took 1 millisecond or more 
* **show databases** – list out all the available databases.

#### Login to MongoDB
```
mongo -u <username> -p <password> --authenticationDatabase <dbname>
```

#### List down users
```
show users;
db.getUsers();
```

#### List down roles 
```
show roles
```

#### List down the collections in current database
```
show collections;
db.getCollectionNames();
````

#### Display records in the collection
1. Get all records 
    ```
      db.<collectionName>.find();
    ```
1. Get limited number of records 
    ```
    db.<collectionName>.find().limit(10);
    ```
1. Get an object by Id
    ```
    db.<collectionName>.find({"_id": ObjectId("someid")});
    ```
1. Count number of records
    ```
    db.<collectionName>.count();
    ```
1. List which fields you want to display 
    ```
    db.<collectionName>.find({"_id": ObjectId("someid")}, {field1: 1, field2: 1});
    db.<collectionName>.find({"_id": ObjectId("someid")}, {field1: 0}); // Exclude 
    ```

#### Insert documents
```
db.<collectionName>.insert([{field1: "value1"}, {field1: "value2"}])
db.<collectionName>.insertMany([{field1: "value1"}, {field1: "value2"}])
```
Example:

```
db.employee.insert({"name":"Ajay Yadav"})
```

#### Save document
Save operation will update if document already exists or it will insert a new document 
```
db.<collectionName>.save({"_id": new ObjectId("jhgsdjhgdsf"), field1: "value", field2: "value"});
```

#### Administrative commands
1. Size of the collection
    ```
    db.<collectionName>.dataSize() 
    ```
1. Total size of document stored in the collection
    ```
    db.<collectionName>.storageSize() 
    ```
1. Total size in bytes for both collection data and indexes
    ```
    db.<collectionName>.totalSize() 
    db.<collectionName>.totalIndexSize() 
    ```
