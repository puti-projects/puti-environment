# puti-environment

Puti environment solution

## Requirements

- Docker
- Docker-compose
- Git

## Usage

### 1. 分支说明
主分支（master）将维护一个包含 Nginx 的分支，包含 Nginx、Puti、DB 的构建。

分支 `puti-db` 已经移除了 Nginx，只包含 Puti 和 一个 DB 容器的构建。


### 2. 安装 Docker，Docker-compose，Git

### 3. 下载 puti-environment

直接 clone：

```sh
git clone https://github.com/puti-projects/puti-environment.git
```

或者下载 zip 压缩包也可以。

### 4. 生成配置文件

```sh
cd puti-environment
cp env-example .env
```
.env 为 puti-environment 项目搭建环境的配置，修改为你希望的配置即可。

```sh
cp nginx/config-example/ /data/nginx/config/
```
请将 Nginx 相关的配置文件放到配置的对应目录（例如此处为 `/data/nginx/config/`，根据自己的配置操作）中，提供了参考配置。

然后就可以开始构建项目和运行服务了。

### 5. docker-compose 构建项目并运行服务

进入 Puti-environment 根目录 （docker-compose.yml 所在目录）：
执行命令：

```sh
docker-compose up
```  

再次启动时可以以守护模式启用，所有容器将后台运行：  

```sh
docker-compose up -d
```

关闭并删除容器：

```sh
docker-compose down
```

停止、启动、重启容器：

```sh
docker-compose stop
docker-compose start
docker-compose restart
```

## Update

如何更新呢？如果是更新 Puti-environment 脚本的话，直接 `git pull` 拉取最近的代码就可以了.

更新到最新的 Puti 版本，只需要拉取最新的 Puti 镜像：

```sh
# 拉取最新版本
docker pull puti/puti
# 拉取指定版本
docker pull puti/puti:v0.1.0
```

每发布一个新版本 release，我们都会维护一个版本对应的镜像，而latest 对应当前 master 分支。

然后重新构建就可以了：

```sh
docker-compose down
docker-compose up -d --build
```
