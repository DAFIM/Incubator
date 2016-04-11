# Image for WSO2 Identity Server, based on 
#  - heribender/java:8_77jre
####################################################


FROM heribender/java:8_77jre
MAINTAINER heribender@web.de

# Install cURL and unzip
RUN apk upgrade --update && \
    apk add --update curl && \
    apk add --update unzip
	
####################################################
# Install WSO2 IS
####################################################
	
# download and unzip WSO2 Identity Server
ENV WSO2IS_VERSION 5.1.0
ENV WSO2IS_HOME_PRE /opt
ENV WSO2IS_HOME ${WSO2IS_HOME_PRE}/wso2is

RUN mkdir ${WSO2IS_HOME_PRE} && \
    curl -o ${WSO2IS_HOME_PRE}/wso2is.zip --user-agent testuser \
    -e http://connect.wso2.com/wso2/getform/reg/new_product_download \
	http://product-dist.wso2.com/products/identity-server/${WSO2IS_VERSION}/wso2is-${WSO2IS_VERSION}.zip

RUN unzip ${WSO2IS_HOME_PRE}/wso2is.zip -d ${WSO2IS_HOME_PRE} \
    && mv ${WSO2IS_HOME_PRE}/wso2is-* ${WSO2IS_HOME} \
    && rm -f ${WSO2IS_HOME_PRE}/wso2is.zip
	
EXPOSE 9443

####################################################
# Configure Postgres DB
####################################################
ENV JDBC_DRIVER postgresql-9.4.1208.jar
RUN curl -o ${WSO2IS_HOME}/repository/components/lib/${JDBC_DRIVER} https://jdbc.postgresql.org/download/${JDBC_DRIVER}
	
# RUN ls -la 	${WSO2IS_HOME}/repository/components/lib
# RUN echo "WSO2_CARBON_DB: ${WSO2_CARBON_DB}"

# RUN cat ${WSO2IS_HOME}/bin/wso2server.sh


# clean up
RUN apk del curl && \
    apk del unzip && \
	rm -rf /var/cache/apk/*

RUN echo "`uname`"
	
#CMD ["${WSO2IS_HOME}/bin/wso2server.sh"]
CMD ["/opt/wso2is/bin/wso2server.sh"]
