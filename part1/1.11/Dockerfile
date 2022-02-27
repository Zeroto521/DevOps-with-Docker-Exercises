FROM openjdk:8

EXPOSE 8080

WORKDIR /usr/src/app

COPY spring-example-project .

RUN apt-get update
RUN apt-get install -y dos2unix
RUN find . -type f -print0 | xargs -0 dos2unix

RUN ./mvnw package

CMD java -jar ./target/docker-example-1.1.3.jar
