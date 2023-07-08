****eureka-server-demo****


This Demo will explain how Eureka discovery server works with Springboot microservices.

We have below microservice:

1. **eureka-client-app-first**  First springboot application running one **9002** port
2. **eureka-client-app-two**    2nd instance of **eureka-client-app-first** running on other port **9003**
3. **feign-load-balancer-ureka-client**   This is Netflix Fiegn-Client Load Balancer for Springboot application ,As a user you want to call some API from a microservice **eureka-client-app**
   
   Here We have 2 Instances of **eureka-client-app** ( **eureka-client-app-first** AND **eureka-client-app-first**)

   As a user whenever you will send some request to **feign-load-balancer-ureka-client** to call some API on **eureka-client-app** THEN **feign-load-balancer-ureka-client** will take care of LOAD BALANCING and it will distribute the call based on node availability.

   SO as a End User you no need to worry for -you are calling API on which instance. LB will take care of it.
   
5. **springboot-ureka-server** : This is Eureka Discovery server.


   **Steps to RUN**

   **DATA FEED**

    1. Install MySQL in you local system, create one DB with NAME test as given in application.properties file.
    2. Start eureka-client-app-first
    3. Open Postman and insert some data using API - **localhost:9003/employee/emp/addEmployee**  [HTTP Method: **POST**]
  
     **Endpoing** localhost:9003/employee/emp/addEmployee
   
     **Payload**:
       {
        "name":"Raj",
        "email":"raj@gmail.com",
        "salary":90000
      }


  **Once you inserted some data in MySQL , proceed as below**

   1. clone all these repos in local system and open it using any IDE.
   2. Start all the servers one by one.
   3. Once ALl are started- try to access **http://localhost:8761/**  ,You will be able to see all the servers details registered to Eureka service registry.
   4. Open Post and call API : **http://localhost:9005/employeeRm/remote/getFeignEmployee/1**   [before running this application insert some data to your DB]

      
  
      
  
      

   
