FROM openjdk:latest as build
RUN yum install git -y
RUN git clone https://github.com/spring-projects/spring-petclinic.git
WORKDIR spring-petclinic
RUN ./mvnw package

FROM openjdk:8-jre-alpine
WORKDIR /home/application/java
COPY --from=build "/spring-petclinic/target/spring-petclinic-2.2.0.BUILD-SNAPSHOT.jar" .
EXPOSE 8080
ENTRYPOINT [ "java", "-jar", "/home/application/java/spring-petclinic-2.2.0.BUILD-SNAPSHOT.jar"]