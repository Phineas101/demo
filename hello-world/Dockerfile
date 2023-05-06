# 使用基础镜像
FROM adoptopenjdk/openjdk11:jdk-11.0.11_9-alpine AS builder

# 声明依赖项
RUN apk update && apk add --no-cache maven

WORKDIR /app

# 复制项目文件到容器中并构建项目
COPY pom.xml .
COPY src/ ./src/
RUN mvn package
