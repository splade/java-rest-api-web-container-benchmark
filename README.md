# java-rest-api-web-container-benchmark
Are you wondering which web container to use for your nest Java REST API?

If your answer is yes, then you are not alone.

This project compares: 
**Tomcat**, **Jetty**, **Grizzly** and **Undertow** in term of serving **JAX-RS** responses

There are 2 blog entries supporting this benchmark:


- http://menelic.com/2016/01/06/java-rest-api-benchmark-tomcat-vs-jetty-vs-grizzly-vs-undertow/

- and http://menelic.com/2016/01/25/java-rest-api-benchmark-tomcat-vs-jetty-vs-grizzly-vs-undertow-round-2/


##Setup
To run this benchmark, you will need:

- The latest Oracle JDK 1.8 or later ( http://www.oracle.com/technetwork/java/javase/downloads ). 
- install apache bench (https://httpd.apache.org/docs/2.2/programs/ab.html ).
 On debian/ubuntu: 
`sudo apt-get install apache2-utils` 

##Running load tests with default server configuration
to run the test, 

- first start the API server by doing:
`./gradlew -p <SERVER NAME> bootRun`
where `<SERVER NAME>` is one of `grizzly`, `jetty`, `tomcat` or `undertow`

- then in a new console, do
`./run-load-test.sh`
feel free to edit the script for for different load profile 

##Changing server thread pool size
One can easily change server thread pool size on the command line: 


####Grizzly 

`./gradlew bootRun -p grizzly -Dserver.grizzly.worker-threads=250`



####Jetty

`./gradlew bootRun -p jetty -Dserver.jetty.min-threads=250 -Dserver.jetty.max-threads=250` 


####Tomcat

`./gradlew bootRun -p tomcat -Dserver.tomcat.max-threads=250`


####Undertow

`./gradlew bootRun -p undertow -Dserver.undertow.worker-threads=250`

#Actuator
To enable spring boot actuator,please look in `build.gradle` for the comments
`/**To enable actuator...`
