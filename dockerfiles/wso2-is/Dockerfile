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

# clean up
RUN apk del curl && \
    apk del unzip && \
	rm -rf /var/cache/apk/*

#CMD ["${WSO2IS_HOME}/bin/wso2server.sh"]
CMD ["/opt/wso2is/bin/wso2server.sh"]
