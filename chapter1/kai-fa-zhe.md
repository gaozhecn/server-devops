# 代码运行环境配置文件

* Docker 版本号
* docker-compose版本号
* node 版本号

建议在 Docker 中运行，做到测试和生产一致。

* Docker
* 主机

分为在 docker 中运行和主机中运行。

# Docker

## docker

### 单个 docker

* 需要提供 Dockerfile文件，用来构建镜像。
* 提供运行该 Dockerfile 文件的脚本\*.sh。

### docker 编排

编排目前建议使用docker-compos，如果是多个 Docker需要和外网进行通信，提供 NGINX 的 Docker 配置，编写进docker-compose.yml 文件中。

* 提供 docker-compose.yml文件。
* 提供运行该 docker-compose.ym 文件的脚本\*.sh。

提交代码，gitlab触发gitlab-runner运行，自动进行编译（如果需要编译），生成镜像，备份到每日构建镜像中，部署到测试服务器中，进行测试。测试成功，都成功的话，合入develop分支（负责人合入），合入之后，触发

