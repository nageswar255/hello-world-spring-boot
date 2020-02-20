
FROM openjdk:8-jdk-alpine
ENV LANG C.UTF-8
ENV MIN_HEAP_SIZE='-Xms1536m' 
ENV MAX_HEAP_SIZE='-Xmx1536m' 
ENV THREADSTACK_SIZE='-Xss512k'
    
ENV JAVA_OPTS=' -server -Duser.timezone=America/Chicago -DDefaultTimeZone America/Chicago -Djava.security.egd=file:/dev/./urandom -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/logs'
ENV JAVA_GC_ARGS='  -XX:+UseConcMarkSweepGC -XX:GCLogFileSize=10M -XX:+UseGCLogFileRotation -XX:+PrintGCTimeStamps -XX:NumberOfGCLogFiles=7 '
ENV JAVA_OPTS_APPEND=''


VOLUME /tmp
RUN mkdir -p /logs
RUN mkdir scripts
RUN chmod 777 /logs
EXPOSE 8080

ADD ./myproject-0.0.1-SNAPSHOT.jar /myproject.jar
ENTRYPOINT ["java","-Dspring.profiles.active=dev","-Dlogging.file=/logs/cbs-test.log","-Dserver.port=8080","-jar","myproject.jar"]

