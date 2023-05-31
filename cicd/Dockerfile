# Use an appropriate base image for Java and Maven
FROM maven:3.8.4-openjdk-16

# Set the working directory inside the container
WORKDIR /app

# Copy the pom.xml file to install dependencies
COPY pom.xml .

# Install project dependencies
RUN mvn dependency:go-offline -B

# Copy the application source code
COPY src ./src

# Build the application
RUN mvn package -DskipTests

# Expose the port that your Spring Boot application listens on
EXPOSE 8080

# Define the command to run your application
CMD ["java", "-jar", "target/cicd-0.0.1-SNAPSHOT.jar"]