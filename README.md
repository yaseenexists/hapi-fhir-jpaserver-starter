# HAPI-FHIR server for Synodex Project

## About the stock project

The author of original project is James Agnew. This project is a customization of [HAPI FHIR JPA server with embedded Java H2 DB](https://github.com/hapifhir/hapi-fhir-jpaserver-starter), to run on mySQL DB, for Innodata's Synodex clients. 

## To run the code locally

In order to use this sample, you should have:

- [This project](https://github.com/yaseenexists/hapi-fhir-jpaserver-starter) cloned and check out the develop branch.

### and 
 - Oracle Java (JDK) installed: Minimum JDK8 or newer.
 - Apache Maven build tool (newest version). 
 - mySQL 5.5 server. 

### Creating the mySQL database
With mySQL server installed, create a database (you will have to use a Admin role for this)  
```bash
CREATE DATABASE hapi_dstu3;
```

### Using Spring Boot with :run
```bash
mvn clean spring-boot:run -Pboot
```
Server will then be accessible at http://localhost:8080/ and eg. http://localhost:8080/fhir/metadata.

### OR Using Spring Boot
```bash
mvn clean package spring-boot:repackage -Pboot && java -jar target/hapi-fhir-jpaserver-starter.war
```
Server will then be accessible at http://localhost:8080/ and eg. http://localhost:8080/fhir/metadata.

## Customizing The Web Testpage UI

The UI that comes with this server is an exact clone of the server available at [http://hapi.fhir.org](http://hapi.fhir.org). You may skin this UI if you'd like. For example, you might change the introductory text or replace the logo with your own.

The UI is customized using [Thymeleaf](https://www.thymeleaf.org/) template files. You might want to learn more about Thymeleaf, but you don't necessarily need to: they are quite easy to figure out.

Several template files that can be customized are found in the following directory: [https://github.com/hapifhir/hapi-fhir-jpaserver-starter/tree/master/src/main/webapp/WEB-INF/templates](https://github.com/hapifhir/hapi-fhir-jpaserver-starter/tree/master/src/main/webapp/WEB-INF/templates)

## Deploying to an Application Server

To deploy to a server

### Build the war file

Clone [this project](https://github.com/yaseenexists/hapi-fhir-jpaserver-starter), checkout the `develop` branch and build the project:

```bash
mvn clean install
```

This will create a file called `hapi-fhir-jpaserver-starter.war` in your `target` directory. This would be the war file to deploy. 

### Creating the mySQL database
With mySQL server installed, create a database by running (you will have to use a Admin role for this) 
```bash
CREATE DATABASE hapi_dstu3;
```

### Configurations 

This flavour of the project uses hard-coded configurations mentioned in [application.yaml](https://github.com/yaseenexists/hapi-fhir-jpaserver-starter/blob/develop/src/main/resources/application.yaml), such as it expects the port of mySQL server to be 3306, the user `root` and password as `root`. Any changes in the setting up of server should be adjusted in this file and the respective .war used for deployment. 

If you would like it to be hosted fhir-jpaserver, eg. http://localhost:8080/hapi-fhir-jpaserver/ or http://localhost:8080/hapi-fhir-jpaserver/fhir/metadata - then rename the WAR file to ```hapi-fhir-jpaserver.war```. 
