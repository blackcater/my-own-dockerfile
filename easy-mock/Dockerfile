# from node 9.4.0
FROM node:9.4.0


# maintainers
LABEL version="1.5.1"
LABEL maintainers="blackcater<blackcater2015@gmail.com>"

ENV EASY_MOCK_VERSION 1.5.1


WORKDIR /

ARG registry=https://registry.npm.taobao.org
ARG source=https://github.com/easy-mock/easy-mock/archive/v${EASY_MOCK_VERSION}.zip

RUN apt-get update && \
	apt-get install unzip && \
	wget -c ${source} -O easy-mock.zip && \
	unzip easy-mock.zip -d / && \
	rm -rf easy-mock.zip && \
	mv easy-mock-${EASY_MOCK_VERSION} easy-mock && \
	cd easy-mock && \
	npm config set registry ${registry} && \
	yarn config set registry ${registry} && \
	yarn global add pm2

WORKDIR /easy-mock

COPY local.json /easy-mock/config/

VOLUME /easy-mock/config/

EXPOSE 7300

RUN yarn install && \
	yarn run build

CMD ["pm2-docker", "start", "app.js"]
