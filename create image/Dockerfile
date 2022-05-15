FROM 192.168.25.203:8080/library/maven:3.8.1-openjdk-17-slim

RUN mkdir -p /root/.m2 \
    && mkdir /root/.m2/repository
# Copy maven settings, containing repository configurations
COPY settings.xml /root/.m2



RUN mvn clean install