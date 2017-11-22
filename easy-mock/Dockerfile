# from node 8.5
FROM node:9.2.0


# maintainers
LABEL version="1.3.5"
LABEL maintainers="blackcater<blackcater2015@gmail.com>"

ENV EASY_MOCK_VERSION 1.3.5


WORKDIR /usr/app

ARG registry=https://registry.npm.taobao.org
ARG source=https://github.com/easy-mock/easy-mock/archive/v${EASY_MOCK_VERSION}.zip

RUN apt-get update && \
	apt-get install unzip && \
	wget -c ${source} -O easy-mock-${EASY_MOCK_VERSION}.zip && \
	unzip easy-mock-${EASY_MOCK_VERSION}.zip && \
	rm -rf easy-mock-${EASY_MOCK_VERSION}.zip && \
	cd easy-mock-${EASY_MOCK_VERSION} && \
	npm config set registry ${registry} && \
	yarn config set registry ${registry} && \
	yarn global add pm2


WORKDIR /usr/app/easy-mock-${EASY_MOCK_VERSION}

COPY local.json /usr/app/easy-mock-${EASY_MOCK_VERSION}/config/

EXPOSE 7300

RUN yarn install && \
	yarn run build

CMD ["pm2-docker", "start", "app.js"]
