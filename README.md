# php7开发环境

## 使用说明

### 安装docker

<https://www.docker.com/get-docker>

### 检出开发项目和docker配置信息

```sh
git clone https://gitee.com/eellydev/api.eelly.com api.eelly.dev
git clone https://gitee.com/eellydev/www www.blty.dev
git clone https://github.com/runphp/docker-php7
# linux
docker run -p 80:80 -p 443:443 -d \
    --name=eelly-php7 \
    -v $PWD:/var/www \
    -v docker-php7/etc/nginx/certs:/etc/nginx/certs \
    -v docker-php7/etc/nginx/conf.d:/etc/nginx/conf.d \
    eelly/php7

# windows 需要绝对路径
docker run -p 80:80 -p 443:443 -d \
    --name=eelly-php7 \
    -v D:/workspace/php:/var/www \
    -v D:/workspace/php/docker-php7/etc/nginx/certs:/etc/nginx/certs \
    -v D:/workspace/php/docker-php7/etc/nginx/conf.d:/etc/nginx/conf.d \
    eelly/php7
```

### 运行composer

```sh
# linux
docker exec -it eelly-php7 composer install -d api.eelly.dev -vvv
# windows
winpty docker exec -it eelly-php7 composer install -d api.eelly.dev -vvv
```