# docker file for tomcat:dubbo-admin
# VERSION 0.1
# Author: chenziqiang

# basic image
FROM tomcat:8.5-jre8

# author
MAINTAINER chenziqiang <czq@itczq.com>

# env
ENV BIN_PATH /usr/local/tomcat/bin
ENV APP_PATH /usr/local/tomcat/webapps
ENV CONF_PATH /usr/local/tomcat/conf
ENV LOG_PATH /usr/local/tomcat/logs
ENV SERVER_CONF_FILE server.xml
ENV USER_CONF_FILE tomcat-users.xml

# delete origin config files
RUN rm $CONF_PATH/$USER_CONF_FILE
RUN rm -rf $APP_PATH/*

# add war to image
ADD ./dubbo-admin.war /root
RUN unzip /root/dubbo-admin.war -d $APP_PATH/ROOT/
RUN rm -rf /root/dubbo-admin.war

# replace dubbo conf file
RUN rm $APP_PATH/ROOT/WEB-INF/dubbo.properties
ADD ./dubbo.properties $APP_PATH/ROOT/WEB-INF/

# run
ENTRYPOINT $BIN_PATH/startup.sh && tail -F $LOG_PATH/catalina.out
