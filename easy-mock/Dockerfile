# from node 8.5
FROM node:8.5.0


# maintainers
LABEL version="1.2.3"
LABEL maintainers="blackcater<blackcater2015@gmail.com>"


WORKDIR /usr/app

ARG registry=https://registry.npm.taobao.org

COPY easy-mock-1.2.3.tar .

RUN tar -xvf easy-mock-1.2.3.tar && \
	cd easy-mock-1.2.3 && \
	npm config set registry ${registry} && \
	yarn config set registry ${registry} && \
	yarn global add pm2


WORKDIR /usr/app/easy-mock-1.2.3

COPY local.json /usr/app/easy-mock-1.2.3/config/

EXPOSE 7300

RUN yarn install && \
	yarn run build

CMD ["pm2-docker", "start", "app.js"]
