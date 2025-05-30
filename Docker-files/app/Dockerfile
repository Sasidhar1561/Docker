FROM ubuntu AS BUILD_IMAGE
WORKDIR /
RUN apt update && apt install git maven openjdk-17-jdk -y
RUN git clone https://github.com/Sasidhar1561/Docker.git
WORKDIR /Docker
RUN MAVEN_OPTS="-Xmx1024m" mvn clean install -DskipTests


FROM tomcat
WORKDIR /usr/local/tomcat
RUN rm -rf webapps/*
COPY --from=BUILD_IMAGE /Docker/target/vprofile-v2.war webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
