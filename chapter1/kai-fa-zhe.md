# 要达到的效果

* 测试和生产的服务武器代码一致，不需要因为特殊的环境配置而修改代码。
* 不在测试服务器和生产服务器上编译镜像，而是从公司镜像仓库拉取镜像（唯一途径）。

* 
* 合入到develop 分支触发编译的镜像，备份到镜像仓库，这个也是测试部获取测试镜像的途径。

# 代码运行环境说明文件

* Docker 版本号
* docker-compose版本号
* node 版本号
* Python 版本号

* ...

* 建议在服务器的服务在Docker 中运行，尽量做到测试和生产一致。

分为在 docker 中运行和主机中运行。

# Docker

### 单个 docker

* 需要提供 Dockerfile文件，用来构建镜像。
* 提供运行该 Dockerfile 文件的脚本\*.sh。
* 其他配置文件。

### docker 编排

目前建议使用docker-compos，如果是多个 Docker需要和外网进行通信，提供 NGINX 的 Docker 配置，编写进docker-compose.yml 文件中。

* 提供 docker-compose.yml文件。
* 提供运行该 docker-compose.ym 文件的脚本\*.sh。

提交代码到gitlab触发gitlab-runner运行，进行编译（如果需要编译），生成镜像，备份到每日构建镜像中，部署到测试服务器中，进行测试，测试成功，成功则合入代码，否则打回代码。

合入develop分支（负责人合入，手动解决冲突），合入之后，触发测试，和上面流程一样。

develop 分支定期或者阶段性合入release 分支。

