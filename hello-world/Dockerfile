################################# Build Container ###############################

# Base Image for Build Container
FROM maven:3.8.6-jdk-11-slim as base

# Moving into working directory
WORKDIR /build

# Copying pom.xml file initially for caching
COPY hello-world/pom.xml .

# Downloading Dependencies 
RUN mvn dependency:go-offline

# Copying files to /build/src/ inside container
COPY hello-world/src/ /build/src/

# Building package 
RUN mvn package

# 建立基于 JRE 的最终映像
FROM openjdk:11-jre

# 暴露端口
EXPOSE 8080

# 将应用程序 Jar 文件复制到运行时映像中
COPY --from=base /build/target/*.jar app.jar

# 执行应用程序
ENTRYPOINT ["java", "-jar", "app.jar"]
