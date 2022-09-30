# docker youtube 1h 课程笔记

## 构建 doocker 需要有以下内容

- a cut-down os
- a runtime environment (eg node)
- Application files
- Third-party libraries
- environment variables

## 创建 Docker 案例

- start with an OS
- install node
- copy an files
- run node app.js

  1.创建 app.js,代码内容为：

```javascript
console.log("hello docker!");
```

2.创建 dockerfile： `Dockerfile`， 代码内容为：

```dockerfile
FROM node:alpine
COPY . /app
WORKDIR /app
CMD node app.js
```

3.终端中打包，运行代码为：

`含义为：在.文件夹（本文件夹），创建`hello-docker`这个名字的image`

```shell
docker build -t hello-docker .


在mac mini 上
docker buildx build --platform linux/arm64 -t xxxx名字 .

--platform linux/amd64 跟上边处理器不一样
```

完成后终端中有提示内容为：

```shell
Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
```

4.此时可以扫描本电脑所有 image 的命令为：

```shell
docker image ls
docker images
```

5.如果运行这个 docker，在终端中输入：

```shell
docker run hello-docker
```

docker 虚拟机网站：[play-with -docker](https://www.docker.com/play-with-docker/)

进入后，进入虚拟机`lab Environment`创建 playground

### docker 本地 image 提交 hub

已有账户 假设 `minus`

已有本地 image 假设叫 `hello-docker`, 其 tag 为`latest`

1.给本地镜像打标签，包括本地镜像名称和线上镜像名称(线上放到 minus/hello 目录下)：

`docker tag hello-docker:latest minus/hello:v1`

2.终端登录 docker，输入 docker login 进行登录 3.推送，指令为`docker push minus/hello:v1` 直到返回一个 digest:sha256:xxxxxx 的哈希值
