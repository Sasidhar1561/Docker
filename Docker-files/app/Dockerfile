FROM ubuntu AS BUILD_IMAGE
WORKDIR /
RUN git clone https://github.com/Sasidhar1561/Docker.git
WORKDIR /Docker/
RUN apt update && apt install maven openjdk-17-jdk -y
RUN mvn clean install


FROM tomcat 
WORKDIR /usr/local/tomcat
RUN rm -rf webapps/*
COPY --from=BUILD_IMAGE /Docker/target/vprofile-v2.war webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]