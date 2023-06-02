# Microservice Cache / Kafka Template

## Microservice Structure

![Package Structure](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/MS-Pkg-Structure.jpg)

### What the Template Provides out of the box

1. Springboot App with Swagger Docs (...adapters.controllers)
2. Exception Handling with Exception Framework using AOP ( ..adapters.aop)
3. Log Management using Logback  (...adapters.filters)
4. Standardized REST Responses (...domain.models.StandardResponse) 
5. Security using JWT Tokens (...adapters.security)
6. Encrypting Sensitive Data using Encryption Algorithms (...security)
7. JPA configurations for H2 and PostgreSQL (...server.config)

### Pre-Requisites 

1. Springboot 3.1
2. Java 17 
3. Jakarta EE (jakarta.servlet.*, jakarta.persistence.*, javax.validation.*)
4. Maven 3.8.6
5. Git 2.31

### Microservice Cache / Kafka Template gives you a 

1. SpringBoot App template with 
2. Open API 3 Ex, 
3. Spring Actuator, 
4. Spring Sleuth and 
5. Redis Cache Implementation with 
6. H2 In Memory Database
7. POM File with (SpringBoot) Fat and Thin (Maven) jar file creation and 
8. Dockerfile for containerisation.

## 1. Setting up the Template

### Step 1.1 - Getting Started

1. git clone https://github.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10.git
2. cd ms-springboot-310-java-17-jakarta-ee-10

###  Step 1.2 - Compile (Once your code is ready) 

#### 1.2.1 Compile the Code
Run the "compile" from ms-springboot-310-java-17-jakarta-ee-10
1. compile OR ./compile (Runs in Linux and Mac OS)
2. mvn clean; mvn -e package; (All Platforms)
3. Use the IDE Compile options

#### 1.2.2 What the "Compile" Script will do

1. Clean up the target folder
2. Generate the build no. and build date (takes application.properties backup)
3. build final output SpringBoot fat jar and maven thin jar
4. copy the jar files (and dependencies) to src/docker folder
5. copy the application.properties file to current folder and src/docker folder

In Step 1.2.2 application.properties file will be auto generated by the "compile" script. This is a critical step.
Without generated application.properties file the service will NOT be running. There is pre-built application properties file.

###  Step 1.3 - Run

#### 1.3.1 Start the Service
1. run OR ./run (Runs in Linux or Mac OS)
2. mvn spring-boot:run (All Platforms)

#### 1.3.2 Test the Service 
1. test OR ./test (Runs in Linux or Mac OS)
2. Execute the curl commands directly (from the test script)

#### $ run Result 
![Run Results](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/MS-Run-Result.jpg)

#### MS Cache Swagger UI Docs for Testing
![Swagger Docs](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/MS-Cache-Swagger-UI.jpg)

### Step 1.4 - Testing the APIs Using Swagger API Docs or Postman

To test the APIs (in secure mode - you will see a lock icon in the Swagger Docs). These test tokens are generated
based on the flag server.token.test=true in the application.properties file. (Change the app.props.tmpl if you want to
change in the build process.) In the Production environment, this flag should be false. These tokens can be generated only in
an Auth Service. All the services need not generate these tokens unless for the developers to test it out.
In a real world scenario, disable (Comment out the function generateTestToken() from the code  java file 
ServiceEventListener.java in the package documentation io.fusion.air.microservice.server.service)  this feature for 
production environment. 

#### Step 1.4.1: Copy the Auth Token
![Authorize Request](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/ms-cache-with-Test-Tokens.jpg)

#### Step 1.4.2: Click on the Authorize Button (Top Left the Swagger UI)

![Authorize Request](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/ms-cache-with-Test-Tokens-2.jpg)

#### Step 1.4.3: Enter the Token and Click Authorize

![Authorize Request](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/ms-cache-with-Test-Tokens-3.jpg)

### Step 1.5 -  Import Swagger API Docs Into Postman

#### Step 1.5.1: Swagger Open API 3.0 Docs JSON Format
![Swagger JSON](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/Import-API-into-Postman-0.jpg)

#### Step 1.5.2: Import Into Postman - Set the Link
![Postman Import](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/Import-API-Into-Postman-1.jpg)

#### Step 1.5.3: Import Into Postman - Confirm
![Postman Import](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/Import-API-into-Postman-2.jpg)

## 2. CRUD Operations Demo & Error Handling

### 2.1 CRUD Operations 

#### 2.1.1 GET Query Execution and Fallback Data
![Crud Get](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-1-get-fallback.jpg)

#### 2.1.2 POST Create Data - Product 1
![Crud Post-1](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-2-post-prod-1-A.jpg)

#### 2.1.3 POST Create Data - Product 1 : Result
![Crud Post-2](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-2-post-prod-1-B.jpg)

#### 2.1.4 POST Create Data - Product 2 
![Crud Post-3](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-3-post-prod-2.jpg)

#### 2.1.5 POST Create Data - Product 3
![Crud Post-4](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-4-post-prod-3.jpg)

#### 2.1.6 GET All the Data (Created in Steps 2.2 - 2.5)
![Crud Get-6](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-5-get-from-db.jpg)

#### 2.1.7 GET Single Record
![Crud Get-7](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-6-get-from-db.jpg)

#### 2.1.8 PUT Update the Product Price
![Crud Get-8](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-7-put-update-price.jpg)

#### 2.1.9 PUT Update the Product - DeActivate the Product > Set isActive Flag = False
![Crud Get-9](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-8-put-deactivate.jpg)

#### 2.1.10 State of the Records after Inserts and Updates
![Crud Get-10](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-9-db-records.jpg)

### 2.2 Error Handling

#### 2.2.1 Error Handling - Invalid Input
![Error-1](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-error-1-post-invalid-input-A.jpg)

#### 2.2.2 Error Handling - Invalid Input - Result
![Error-2](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-error-1-post-invalid-input-B.jpg)

#### 2.2.3 Error Handling - Invalid Input - Field Validations
![Error-3](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-error-2-post-invalid-input-A.jpg)

#### 2.2.4 Error Handling - Invalid Input - Field Validations - Result
![Error-4](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-error-2-post-invalid-input-B.jpg)

#### 2.2.5 Error Handling - Version Mismatch based o JPA @Version Annotation
![Error-5](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/crud/crud-error-3-post-Version-Mismatch-B.jpg)


### 2.3 Log Management 

#### 2.3.1 Log Success Messages
![Log-1](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/log/Log-Messages-1.jpg)

#### 2.3.2 Log Failure Messages
![Log-2](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/log/Log-Messages-2.jpg)

## 3. Configure the Template: Setup Org, Service, & Container Name, Versions, API Path in app.props.tmpl

1. git clone https://github.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10.git
2. cd ms-springboot-310-java-17-jakarta-ee-10

Update the Properties Template

1. Update the Org Name in src/main/resources/app.props.tmpl file (service.org)
2. Update the Microservice name in src/main/resources/app.props.tmpl file (service.name)
3. Update the API Version in src/main/resources/app.props.tmpl file (service.api.version)
4. Update the API Name in src/main/resources/app.props.tmpl file (service.api.name)
5. Update the Container Name in src/main/resources/app.props.tmpl file (service.container)
6. Update the Server Version src/main/resources/app.props.tmpl file (server.version)
   Pom File
   <version>0.4.0</version>
   app.props.tmpl
   Microservice Server Properties
   server.version=0.4.0

Sample Property File Template
![Property File](https://raw.githubusercontent.com/arafkarsh/ms-springboot-310-java-17-jakarta-ee-10/master/diagrams/MS-Property-File.jpg)

When you change the version in POM.xml, update that info in src/main/resources/app.props.tmpl - server.version property also.

## 4. Docker Container Setup

### Step 4.1 - Verify Container Name and Org Name

1. Verify the Org Name in src/main/resources/app.props.tmpl file (service.org)
2. Verify the container name in src/main/resources/app.props.tmpl file (service.container)
3. Verify the microservice name in src/main/resources/app.props.tmpl file (service.api.name)

### Step 4.2 - Build the image

1. build (Build the Container)
2. scan (Scan the container vulnerabilities)

### Step 4.3 - Test the image

1. start (Start the Container)
2. logs (to view the container logs) - Wait for the Container to Startup
3. Check the URL in a Browser

### Step 4.4 - Push the image to Container Cloud Repository

Update the Org Name in src/main/resources/app.props.tmpl file (service.org)
Setup the Docker Hub or any other Container Registry

1. push (Push the Container to Docker Hub)

### Step 4.5 Other Commands

1. stop (Stop the Container)
2. stats (show container stats)


(C) Copyright 2022 : Apache 2 License : Author: Araf Karsh Hamid
