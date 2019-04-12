# 软件组-服务器端-版本流程以及运维管理

* devops

* 容器化

* 交付代码--&gt;交付镜像

# 要达到的效果

* 开发、测试、生产的服务器所用的代码一致，不需要因为特殊的环境配置而修改代码。
* 在公司本地（或者云上）搭建镜像编译以及运行环境，develop 分支编译、测试通过，生成镜像，备份到镜像仓库。

* ss

* 不在测试服务器和生产服务器上编译镜像，而是从公司镜像仓库拉取镜像（唯一途径）。

* 服务器上没有代码，只有各种配置文件。

* 合入到develop 分支触发编译的镜像，备份到镜像仓库，这个也是测试部获取测试镜像的途径。

# 



