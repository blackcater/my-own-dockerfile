# from node 8.5
FROM node:8.5.0


# maintainers
LABEL version="1.3.0"
LABEL maintainers="blackcater<blackcater2015@gmail.com>"

ENV EASY_MOCK_VERSION 1.3.0


WORKDIR /usr/app

ARG registry=https://registry.npm.taobao.org

COPY easy-mock-${EASY_MOCK_VERSION}.tar .

RUN tar -xvf easy-mock-${EASY_MOCK_VERSION}.tar && \
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
