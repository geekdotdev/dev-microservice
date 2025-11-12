# dev-microservice
DevContainer enabled microservice 

# DevContainer JSON reference:
https://containers.dev/implementors/json_reference/

# Available Features:
https://containers.dev/features

# From Scratch Setup:
spring init --name microsvc --java-version=21 --package-name=com.geek.dev --group=com.geek.dev --artifact=hello-api-aggregation --type=maven-project microsvc 

In Project Settings, Project Structure:
    delete the dev container root as a Content Root
    Modules + -> Select microsvc -> Next
        Import from external model: maven 
Add org.springframework.boot.spring-boot-starter-web dependency, but exclude org.springframework.boot.spring-boot-starter-logging
Add org.springframework.boot.spring-boot-starter-log4j2
Add org.projectlombok.lombok dependency
Right click the microsvc folder -> maven -> sync

cd into the java projects dir, microsvc
Create a Dockerfile
Delete the .gitignore and .gitattributes
Add rest package containing a RestController class. Do not call the class 'RestController'
mvn clean install

# Do it again for utilsvc
spring init --name utilsvc --java-version=21 --package-name=com.geek.dev --group=com.geek.dev --artifact=util-api --type=maven-project utilsvc 

# Build deployable jar:
mvn clean package spring-boot:repackage -Dmaven.test.skip=true

# Run it:
java -jar target/hello-api-aggregation-0.0.1-SNAPSHOT.jar --spring.profiles.active=local
