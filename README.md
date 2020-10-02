# SOAP Microservices with Spring Boot and Apache CXF
*Soap endpoint for ws-employee*

Spring Boot Microservices and AWS Cloud development 

The tech stack for this POC is:
* Spring Boot 2.3.4
* Java 15
* Apache CXF 3.4
* Docker
 
## Requirements
* Java 15 JDK - https://jdk.java.net/15/
* Maven - https://maven.apache.org/download.cgi

**Optional tools**
* Docker - https://www.docker.com/products/docker-desktop
* Docker hub account with token access enabled

Go to my Java Windows Installation Cheat Sheet ![T.B.D](https://github.com/jpontdia/ws-employee)

## WSDL and XSD
Next is the WSDL diagram:
![WSDL Diagram](/doc/wsdl-diagram.png)

Next is the XSD schema:
![XSD Schema](/doc/xsd-employeesresponse.png)

![XSD Schema](/doc/xsd-employeebynamerequest.png)

![XSD Schema](/doc/xsd-employeebyidrequest.png)

The wsdl file [definition](/src/main/resources/wsdl/EmployeeServices.wsdl)

## Installation and build

Make sure your computer is configured with the tools in the requirements section.

In order to run the project type in project root folder:
```bash
mvn spring-boot:run
```

Build
## Usage
The list of services are available under:
```html
http://localhost:8081/soap
```

The employee wsdl file is here:
```html
http://localhost:8081/soap/service/employee?wsdl
```

## Docker Image
Create the jar file of the service:
```bash
mvn install
```

Log in into your Docker Hub account ussing the access token:
```bash
docker login --username=YOUR_ACCOUNT
```

Example:
```bash
C:\workspace\dev\datajdbc\ws-employee-soapcxf>docker login --username=jpontdia
Password:
Login Succeeded
```

Create docker image
```bash
docker build --build-arg JAR_FILE=target/*.jar --tag jpontdia/ws-employee-soapcxf .
```

You should see the message: Successfully tagged jpontdia/ws-employee-soapcxf:latest. Example:
```bash
C:\workspace\dev\datajdbc\ws-employee-soapcxf>docker build --build-arg JAR_FILE=target/*.jar --tag jpontdia/ws-employee-soapcxf .
Sending build context to Docker daemon  29.24MB
Step 1/5 : FROM adoptopenjdk/openjdk15:x86_64-alpine-jre-15_36
x86_64-alpine-jre-15_36: Pulling from adoptopenjdk/openjdk15
df20fa9351a1: Pull complete
485bef740c7c: Pull complete
7b26ca94da60: Pull complete
Digest: sha256:a9b20bbb07ce018260effe2113bf2f3074739afde501df615e22745df3b48571
Status: Downloaded newer image for adoptopenjdk/openjdk15:x86_64-alpine-jre-15_36
 ---> edc28ff1032d
Step 2/5 : VOLUME /tmp
 ---> Running in c6ecbb27be28
Removing intermediate container c6ecbb27be28
 ---> b6c2c51f1532
Step 3/5 : ARG JAR_FILE
 ---> Running in 193ef5bb8a6a
Removing intermediate container 193ef5bb8a6a
 ---> c4e12e3e67b2
Step 4/5 : COPY ${JAR_FILE} app.jar
 ---> 7a799bce3230
Step 5/5 : ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
 ---> Running in ff3eb68c9c64
Removing intermediate container ff3eb68c9c64
 ---> c2b63024196e
Successfully built c2b63024196e
Successfully tagged jpontdia/ws-employee-soapcxf:latest
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.
```

Verify the image was created correctly
```bash
docker images

REPOSITORY                     TAG                       IMAGE ID            CREATED             SIZE
jpontdia/ws-employee-soapcxf   latest                    c2b63024196e        19 minutes ago      221MB
adoptopenjdk/openjdk15         x86_64-alpine-jre-15_36   edc28ff1032d        9 days ago          192MB
```

Push image to Docker Hub

```bash
docker push jpontdia/ws-employee-soapcxf

The push refers to repository [docker.io/jpontdia/ws-employee-soapcxf]
a5988eef4f17: Pushed
8ec501d69d1a: Mounted from adoptopenjdk/openjdk15
41eb7e916580: Mounted from adoptopenjdk/openjdk15
50644c29ef5a: Mounted from jpontdia/ws-employee
latest: digest: sha256:f414594938049532b74fff2bd3c63269c9322de5c83007d8b42a5f46f1b93ec6 size: 1163

```





## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[![License](https://img.shields.io/badge/License-Apache%202.0-yellowgreen.svg)](https://opensource.org/licenses/Apache-2.0)