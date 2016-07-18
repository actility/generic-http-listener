# generic-http-listener

Example of a simple Java HTTP listener, useful for all ThingPark notifications and callbacks.

The program listens to all HTTP/HTTPS requests targeted to a specific port. By default that port is 9080 for HTTP and 9443 for HTTPS, which means that ThingPark should be configured to target http://listenerhost:9080 or https://listenerhost:9443 to send its notifications and callbacks.

All HTTP requests will be captured:
- requests using methods GET, POST, PUT, DELETE, PATCH or OPTIONS
- requests targetting the root URI / or any other URI such as /subscribe, /post/some/body, etc
- requests using query parameters (?param=xxx) or HTTP headers (Content-type, etc)
- requests having a body

For each HTTP request, all information above will be logged. The details of the last 10 requests can be accessed either in the listener logs, or by accessing the following GET URI e.g. with a browser with HTTP:
`http://listenerhost:9080/generic-http-listener/last-requests`

This listener can be used for demo purposes or to initiate your own specific ThingPark integration component.

### Requirements
The listener relies on the Spring Boot framework, which means it requires Java 7+ to run and Maven 3.2+ to be built.

### How to build
In order to build the listener, the following command should be used at the root of the generic-http-listener folder:
```
mvn package spring-boot:repackage
```

### How to run
Once the listener jar has been built, the following command can be used to start listening:
```
java -jar generic-http-listener.jar
```
### Customization
The default HTTPS listening port and keystore properties can be changed in properties file `src/main/resources/application.properties`.
The default HTTP listening port can be changed in Java file `com.actility.lab.generichttplistener.ServerRunner.java`.
