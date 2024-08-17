FROM openjdk:17
COPY /target/*.jar assurancepolicy-service.jar
EXPOSE 8060
ENTRYPOINT ["java", "-jar", "assurancepolicy-service.jar"]