# SOAP Microservices with Spring Boot and Apache CXF
*Soap endpoint for ws-employee*

Spring Boot Microservices and AWS Cloud development 

The tech stack for this POC is:
* Spring Boot 2.3.3
* Java 14
* Apache CXF 3.4
* AWS Platform: ECR, ECS, Fargate
 
### Local environment requirements
* Java 14 JDK - https://openjdk.java.net/projects/jdk/14/
* Maven - https://maven.apache.org/download.cgi
* Docker - https://www.docker.com/products/docker-desktop

### WSDL and XSD
Next is the WSDL diagram:
![WSDL Diagram](/doc/wsdl-diagram.png)

Next is the XSD schema:
![XSD Schema](/doc/xsd-employeesresponse.png)

![XSD Schema](/doc/xsd-employeebynamerequest.png)

![XSD Schema](/doc/xsd-employeebyidrequest.png)

The wsdl file [definition](/src/main/resources/wsdl/EmployeeServices.wsdl)