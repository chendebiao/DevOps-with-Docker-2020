FROM openjdk:8

WORKDIR /mydir

RUN apt-get update && apt-get install -y git

RUN git clone https://github.com/docker-hy/spring-example-project .

# Expose port 8080
EXPOSE 8080

RUN ./mvnw package

ENTRYPOINT ["java", "-jar"]
CMD ["./target/docker-example-1.1.3.jar"]
