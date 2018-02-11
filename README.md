# 自己用的一些`Dockerfile`
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fblackcater%2Fdocker.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fblackcater%2Fdocker?ref=badge_shield)


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

`easy-mock`依赖于`mongodb`和`redis`，首先安装`mongodb`和`redis`

```
$ docker pull mongo
$ docker run -itd -p 27017:27017 --name mongo mongo
$ docker pull redis
$ docker run -itd -p 6379:6379 --name redis redis
```

安装`easy-mock`

```
$ docker pull blackcater/easy-mock
$ docker run -it -p 7300:7300 \
             --link mongo:mongo \
             --link redis:redis \
             --name easy-mock \
             -d blackcater/easy-mock
```

之后，访问`localhost:7300`即可

如果你想要覆盖 `config/local.json` 文件，请按下面命令安装`easy-mock`

```
$ docker pull blackcater/easy-mock
$ docker run -it -p 7300:7300 \
             --link mongo:mongo \
             --link redis:redis \
             -v /easy-mock/conf:/easy-mock/conf \
             --name easy-mock \
             -d blackcater/easy-mock
```


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fblackcater%2Fdocker.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fblackcater%2Fdocker?ref=badge_large)