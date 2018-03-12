# from node 9.4.0
FROM node:9.6.0


# maintainers
LABEL version="1.0.0"
LABEL maintainers="blackcater<blackcater2015@gmail.com>"

ENV BC_NODE_VERSION 1.0.0


WORKDIR /

ARG registry=https://registry.npm.taobao.org

RUN curl -L https://unpkg.com/@pnpm/self-installer | node && \
  npm config set registry ${registry} && \
	yarn config set registry ${registry} && \
	npm install -g pnpm && \
	pnpm config set registry ${registry}

WORKDIR /workspace

VOLUME /workspace
