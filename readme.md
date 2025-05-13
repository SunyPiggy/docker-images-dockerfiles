自带时区设置的镜像
nginx
redis
在docker-compose.yml文件中通过设置环境变量即可设置时区
environment:
      - TZ=Asia/Shanghai