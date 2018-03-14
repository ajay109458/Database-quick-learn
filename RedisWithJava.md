# Redis with Java

## Configuration 

1. Download JAR
* [Download Jedis.jar](http://repo1.maven.org/maven2/redis/clients/jedis/2.1.0/jedis-2.1.0-sources.jar)

2. Maven entry
```
<dependency>
    <groupId>redis.clients</groupId>
    <artifactId>jedis</artifactId>
    <version>2.9.0</version>
</dependency>
```

## Sample Application for Redis with Java
```
import redis.clients.jedis.Jedis; 

public class RedisStringJava { 
   public static void main(String[] args) { 
      //Connecting to Redis server on localhost 
      Jedis jedis = new Jedis("localhost"); 
      System.out.println("Connection to server sucessfully"); 
      
      //set the data in redis string 
      jedis.set("tutorial-name", "Redis tutorial"); 
      
      // Get the stored data and print it 
      System.out.println("Stored string in redis:: "+ jedis.get("tutorialname")); 
   } 
}
```
