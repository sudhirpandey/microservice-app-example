FROM openjdk:8-alpine AS builder
WORKDIR /usr/src/app
COPY pom.xml mvnw ./
COPY .mvn/ ./.mvn
RUN ./mvnw dependency:resolve
COPY . .
RUN ./mvnw install



FROM openjdk:8-alpine
EXPOSE 8083
WORKDIR /usr/src/app
COPY --from=builder /usr/src/app/target/users-api-0.0.1-SNAPSHOT.jar .
CMD ["java", "-jar", "users-api-0.0.1-SNAPSHOT.jar"]  
