################################# Build Container ###############################

# Base Image for Build Container
FROM maven:3.5.3-jdk-8-alpine as base

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
