# puti-environment
Puti environment solution   
非拉取镜像的本地构建分支。

## Requirements
- Docker
- Docker-compose
- Git

## Usage
### 1. 安装 Docker，Docker-compose，Git 

### 2. 下载 puti-environment
直接 clone：
```
git clone https://github.com/puti-projects/puti-environment.git
```
或者下载 zip 压缩包也可以。
### 3. 下载 Puti 项目，生成配置文件
```
cd puti-environment
cp env-example .env

cd app
git clone https://github.com/puti-projects/puti.git
```
.env 为 puti-environment 项目搭建环境的配置，自行修改配置。

### 4.docker-compose 构建项目并运行服务
进入 docker-compose.yml 所在目录：
执行命令：
```
docker-compose up
```  

如果没问题，下次启动时可以以守护模式启用，所有容器将后台运行：  
```
docker-compose up -d
``` 
关闭容器并删除服务：
```
docker-compose down
```