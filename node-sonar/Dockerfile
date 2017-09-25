#
# Gitlab Dockerfile.
#
# Custom docker image with some important npm modules.
#

FROM java:8-jre


# maintainers
LABEL version="1.0.0"
LABEL maintainers="blackcater<blackcater2015@gmail.com>"


# asncy node env
ARG NODE_ENV
ARG registry=https://registry.npm.taobao.org
ENV NODE_ENV $NODE_ENV

# install nodejs
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash - && \
	apt-get install -y nodejs && \
	npm install -g yarn && \
	npm config set registry ${registry} && \
	yarn config set registry ${registry}


# sonar-scanner workdir
WORKDIR /usr/local

# install sonar-scanner
ENV SONAR_SCANNER_VERSION 3.0.3.778

# download sonar-scanner and install
RUN wget https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-${SONAR_SCANNER_VERSION}.zip && \
    unzip sonar-scanner-cli-${SONAR_SCANNER_VERSION}.zip && \
    rm sonar-scanner-cli-${SONAR_SCANNER_VERSION}.zip

# copy sonar-scanner.properties
COPY sonar-scanner.properties /usr/local/sonar-scanner-${SONAR_SCANNER_VERSION}/conf/

# add sonar-scanner to PATH
ENV PATH /usr/local/sonar-scanner-${SONAR_SCANNER_VERSION}/bin:${PATH}


# set work dir
WORKDIR /usr/src/app
