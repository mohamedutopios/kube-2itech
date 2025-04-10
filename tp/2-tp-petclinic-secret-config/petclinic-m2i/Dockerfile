FROM eclipse-temurin:21-jdk-jammy
WORKDIR /app
COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN ./mvnw dependency:resolve
COPY src ./src
EXPOSE 8080
CMD ["./mvnw", "spring-boot:run"] 

# FROM eclipse-temurin:21-jre-jammy
# EXPOSE 8080
# COPY --from=build /app/target/spring-petclinic-*.jar /spring-petclinic.jar
# CMD ["java", "-jar", "spring-petclinic.jar"]