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

## Database 

#### Create a database
It will create database if it doesn't exists.
```
use <database>
```
Example:
```
use hotel
```

#### Drop database
```
db.dropDatabase()
```

#### List down the collections in current database
```
show collections;
db.getCollectionNames();
````

## Collection

#### Create a collection
```
db.createCollection("employee")
```

#### Drop a collection
```
db.employee.drop()
```

## Document

#### Display records in a collection
1. Get all records 
    ```
      db.<collectionName>.find();
    ```
1. Get all records in pretty format
    ```
      db.<collectionName>.find().pretty();
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

#### Remove documents
Remove depending on filter criteria
```
db.employee.remove({'title':'Software Developer'})
```
Remove all documents
```
db.employee.remove()
```

#### Projection 
Values to display from a document as part of find command output.
```
db.employee.find({},{"title":1,_id:0})
```

#### Skip 
Number of documents to skip
```
db.employee.find().limit(10).skip(5)
```

#### Sort
Sort the output of find command on basis of some property of document
```
db.employee.find().sort({name:1})
```
Note: 1 for sorting in ascending order and -1 for sorting in descending order.

#### Create Index 
```
db.employee.ensureIndex({"title":1})
```

## Administrative commands
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
    
## Sample Application : MongoDB integration with Java
* Download mongo.jar and import in java project library

#### Sample code
```
import com.mongodb.client.MongoDatabase; 
import com.mongodb.MongoClient; 
import com.mongodb.MongoCredential;  

public class MongoDBSampleApplication { 
   
   public static void main( String args[] ) {  
      
      // Creating a Mongo client 
      MongoClient mongo = new MongoClient( "localhost" , 27017 ); 
   
      // Creating Credentials 
      MongoCredential credential; 
      credential = MongoCredential.createCredential("username", "databasename", 
         "password".toCharArray()); 
      System.out.println("Connected to the database successfully");  
      
      // Accessing the database 
      MongoDatabase database = mongo.getDatabase("databasename"); 
      System.out.println("Credentials ::"+ credential);  
      
      // Create collection 
      database.createCollection("firstcollection"); 
      
      // Get documents from collection
      MongoCollection<Document> collection = database.getCollection("firstcollection);
      
      // Insert a document in the collection
      Document document = new Document("title", "Software Developer") 
      .append("id", 1)
      .append("name", "Ajay Yadav") 
      .append("age", 26) 
      .append("by", "Ajay Yadav");  
      
      collection.insertOne(document); 

   } 
}
```
