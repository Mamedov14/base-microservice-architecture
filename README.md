# base-microservice-architecture

## Create Eureka Server

Навесить аннотацию **@EnableEurekaServer** на запускаемый класс

Пример:
```java  
import org.springframework.boot.SpringApplication;  
import org.springframework.boot.autoconfigure.SpringBootApplication;  
import org.springframework.cloud.netflix.eureka.server.EnableEurekaServer;  
  
@SpringBootApplication  
@EnableEurekaServer  
public class EurekaServerApplication {  
	public static void main(String[] args) {       			 
		SpringApplication.run(EurekaServerApplication.class, args);    
	}
}  
```  

Базовый вид application.properties:

```properties  
server.port=8761  
  
eureka.client.register-with-eureka=false  
eureka.client.fetch-registry=false  
```  

По умолчанию Eureka поднимается на порту 8761

## Create Eureka Client

Навесить аннотацию **@EnableEurekaClient** на запускаемый класс

```java
import org.springframework.boot.SpringApplication;  
import org.springframework.boot.autoconfigure.SpringBootApplication;  
import org.springframework.cloud.netflix.eureka.EnableEurekaClient;  
  
@SpringBootApplication  
@EnableEurekaClient  
public class EurekaClientApplication {  
    public static void main(String[] args) {  
        SpringApplication.run(EurekaClientApplication.class, args);  
    }  
}
```

Базовый вид application.properties:

```properties  
server.port=0

spring.application.name=client  
eureka.instance.instance-id=${spring.application.name}:${random.uuid}
```  

+ server.port=0 - создаст порт при поднятие сервера
+ spring.application.name - задаёт имя, чтобы Eureka Server знал о существовании клиента
+ eureka.instance.instance-id - создаёт уникальный id если поднимется несколько экземпляров данного клиента


