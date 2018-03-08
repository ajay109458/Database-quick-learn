## MongoDB integration with Java
* Download mongo.jar and import in java project library

#### Sample Application
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
