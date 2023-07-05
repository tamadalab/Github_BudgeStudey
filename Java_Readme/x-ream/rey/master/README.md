# rey
   [http://rey.xream.io](http://rey.xream.io) 
   
[![license](https://img.shields.io/github/license/x-ream/rey.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)
[![maven](https://img.shields.io/maven-central/v/io.xream.rey/rey.svg)](https://search.maven.org/search?q=io.xream)
[![Gitter](https://badges.gitter.im/x-ream/x-ream.svg)](https://gitter.im/x-ream/community)

### GLIMPSE 

       rey
             @EnableReyClient           @ReyClient
             @EnableFallback            @Fallback
             
             @Resource private ReyTemplate reyTemplate;
        
       rey-spring-boot-starter
       
       rey-seata-spring-boot-starter

```xml        
    <dependency>
         <groupId>io.xream.rey</groupId>
         <artifactId>rey-spring-boot-starter</artifactId>
         ....
    </dependency>
```         
       
### NOTES   
       1. @Fallback not dependent on remote call, can add fallback on any class
       2. @ReyClient, call remote service, if get exception, will respond exception message with
           status 222, while actual status in message body
       3. If deploy many copies of a set of microservices, how to route to the service?
```java          
            public class FooRouter implements GroupRouter{
                 public String replaceHolder(){
                      return "#xxx#";
                 }
                 public String replaceValue(Object obj) {
                      // See the demo: CatServiceGroupRouterForK8S.java
                      // Anyway, coding to ensure all the data only in the dbs connected by the target services
                      // each set of services connect diffent db and cache, one set include: storage, db, cache, 
                      // and your program 
                      // all in docker, all in k8s, set/k8s namespace
                 }
            }
```

```java
            import org.springframework.web.bind.annotation.RequestMapping;
            
            @ReyClient(value = "http://${app.foo}/xxx", groupRouter = FooRouter.class)
            public interface barRemote {
                @RequestMapping("/test")
                String test();
            }      
```        
            config:
            # when write/read db, sharding db can't support more TPS
            # we set the k8s namespace: prod_0, prod_1, prod_2 ....
            # k8s ingress to front service(no connection to DB), front service call service-demo
            # by this way, one set of services' TPS is 10000, deploy 10 sets, TPS become almost 100000
            service.demo=service-demo.prod#xxx#
            
 ### CODING ERROR
       1. annotation Fallback And CircuitBreaker(resilience4j) on the same class:
```java
            @RestController
            @RequestMapping("/soo")
            @CircuitBreaker(name = "soo")
            @Fallback(fallback = SooFallback2.class, ignoreExceptions = {
                    IllegalArgumentException.class,
                    ReyBizException.class
                    })
            public class SooController {
                // ...
            }
```
       2.  annotation Fallback on class, while CircuitBreaker(resilience4j) on a method of the class:
```java
            @RestController
            @RequestMapping("/soo")
            @Fallback(fallback = SooFallback2.class, ignoreExceptions = {
                    IllegalArgumentException.class,
                    ReyBizException.class
                    })
            public class SooController {
            
                @CircuitBreaker(name = "soo")
                @RequestMapping("/aaa")
                public String aaaaa() {
                    return null;
                }
            }
```