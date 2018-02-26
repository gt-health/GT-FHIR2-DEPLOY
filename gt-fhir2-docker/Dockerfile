FROM tomcat:alpine
MAINTAINER Mike Riley "Michael.Riley@gtri.gatech.edu"

RUN apk update
RUN apk add zip postgresql-client

RUN mkdir -p "/opt/app"
ADD GT-FHIR2/gt-fhir2-server/target/gt-fhir2-server.war /opt/app/gt-fhir.war

# Copy GT-FHIR war file to webapps.
RUN cp /opt/app/gt-fhir.war $CATALINA_HOME/webapps/
RUN mkdir -p $CATALINA_HOME/webapps/gt-fhir/ && cd $CATALINA_HOME/webapps/gt-fhir/ && unzip $CATALINA_HOME/webapps/gt-fhir.war

COPY wait-for-postgres.sh /usr/local/bin/wait-for-postgres.sh
RUN chmod +x /usr/local/bin/wait-for-postgres.sh

EXPOSE 8080:8080
