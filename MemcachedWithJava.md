# Memcached with Java

## Configuration 
1. Download JAR
* [Download Memcached JAR](https://mvnrepository.com/artifact/net.spy/spymemcached/2.12.3)
2. Maven entry
```
<!-- https://mvnrepository.com/artifact/net.spy/spymemcached -->
<dependency>
    <groupId>net.spy</groupId>
    <artifactId>spymemcached</artifactId>
    <version>2.12.3</version>
</dependency>
```

## Sample Application with Memcached
```
import net.spy.memcached.MemcachedClient;
public class MemcachedJava {
   public static void main(String[] args) {
      
      // Connecting to Memcached server on localhost
      MemcachedClient mcc = new MemcachedClient(new
      InetSocketAddress("127.0.0.1", 11211));
      System.out.println("Connection to server sucessfully");
      
      //not set data into memcached server
      System.out.println("set status:"+mcc.set("tutorialspoint", 900, "memcached").done);
      
      //Get value from cache
      System.out.println("Get from Cache:"+mcc.get("tutorialspoint"));
   }
}
```
