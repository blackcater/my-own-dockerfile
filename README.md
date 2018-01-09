
# 自己用的一些`Dockerfile`

## 目录

- [`node-sonar`](https://github.com/blackcater/docker/tree/master/node-sonar)
- [`easy-mock`](https://github.com/blackcater/docker/tree/master/easy-mock)

## 使用说明

### `node-sonar`

> 具有`node`环境和`sonar-scanner`环境。

```
$ docker pull blackcater/node-sonar
$ docker run -it --name node-sonar -d blackcater/node-sonar
```

### `easy-mock`

> 对`easy-mock`进行封装

`easy-mock`依赖于`mongodb`，首先安装`mongodb`

```
$ docker pull mongo
$ docker run -it --name mongo -d mongo
```

安装`easy-mock`

```
$ docker pull blackcater/easy-mock
$ docker run -it -p 7300:80 
             --link mongo --name easy-mock 
             -d blackcater/easy-mock
```

之后，访问`localhost:7300`即可
