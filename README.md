# Spring microservices communication using feign client
Steps which needs to be followed are as :-

- Eureka Server creation
- Create Hello Server and register it with Eureka
- Create Hello Client and communicate with Hello server using Feign

## Eureka Server creation
- Create Maven project and add the required dependencies such as:
  - spring-cloud-starter-netflix-eureka-server
  - spring-boot-starter-test

 - Create application.properties and add,

   ```
   server.port="give any value default 8761"
   eureka.client.register-with-eureka=false
   eureka.client.fetch-registry=false
   ```
   
 - Add EnableEurekaServer annotation in your Application class.
 - Finally run the application class and hit the url http://localhost:8761

## Create Hello Server and register it with Eureka
-  Create maven project and add the required dependencies such as:
   - spring-cloud-starter-netflix-eureka-client
   - spring-boot-starter-web
     
-  Create application.properties and add,
  
      ```
      server.port="give any value default (we are using 8071)"
      spring.application.name=hello-service 
      eureka.client.register-with-eureka=true 
      eureka.client.fetch-registry=true 
      eureka.client.serviceUrl.defaultZone:http://localhost:8761/eureka/ 
      eureka.instance.hostname:localhost
      ```

-  Add EnableDiscoveryClient annotation in your Application class.
-  Add Rest Controller and create method and return any String.
  

Finally run the application and if want to check your application hit the url http://localhost:8071/rest/hello/server

## Create Hello Client and communicate with Hello server using Feign
-  Create maven project and add the required dependencies such as:
   -  spring-cloud-starter-netflix-eureka-client
   -  spring-boot-starter-web and spring-cloud-starter-feign
     
-  Create application.properties and add, 

      ```
      server.port="give any value default (we are using 8072)"
      spring.application.name=hello-client 
      eureka.client.register-with-eureka=true 
      eureka.client.fetch-registry=true 
      eureka.client.serviceUrl.defaultZone:http://localhost:8761/eureka/ 
      eureka.instance.hostname:localhost
      ```
      
-  Add EnableDiscoveryClient and EnableFeignClients annotation in your Application class.
-  Add interface and annotated it with FeignClient annotation.
-  Add Rest Controller and call hello service using feign client interface.

Finally run the application and hit the url http://localhost:8072/rest/hello/client


