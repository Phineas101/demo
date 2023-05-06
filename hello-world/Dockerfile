WORKDIR /app

# 复制项目文件到容器中并构建项目
COPY pom.xml .
COPY src/ ./src/
RUN mvn package
