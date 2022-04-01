FROM docker.io/adoptopenjdk/openjdk16-openj9:x86_64-alpine-jre-16.0.1_9_openj9-0.26.0
RUN apk update && \
    apk fetch libssh2 && \
    apk add ./libssh2-1.8.1-r0.apk && \
    apk fetch libcurl && \
    apk add ./libcurl-7.61.1-r2.apk && \
    apk fetch curl && \
    apk add ./curl-7.61.1-r2.apk && \
    rm -rf /var/cache/apk/

COPY target/quarkus-app/lib/ /deployments/lib/
COPY target/quarkus-app/*.jar /deployments/
COPY target/quarkus-app/quarkus/ /deployments/quarkus/
COPY target/quarkus-app/app/ /deployments/app/

CMD ["java", "-jar", "-Dquarkus.http.host=0.0.0.0", "-Djava.util.logging.manager=org.jboss.logmanager.LogManager", "/deployments/quarkus-run.jar"]
