## Stage 1 - compile code and build jar
FROM openjdk:8 as builder
RUN mkdir /opt/complete
WORKDIR /opt/complete
COPY ./complete /opt/complete
RUN ls -lt /opt/complete
RUN ./gradlew build
RUN ls -ltR /opt/complete/build

## Stage 2 - copy jar and configure runtime
FROM openjdk:8
WORKDIR /root/
COPY --from=builder /opt/complete/build/libs/gs-spring-boot-0.1.0.jar .
#ENTRYPOINT ["tail", "-f", "/dev/null"]
ENTRYPOINT ["java", "-jar", "/root/gs-spring-boot-0.1.0.jar"]
