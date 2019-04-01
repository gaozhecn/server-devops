# 意义

* 正规，职责分离，服务器只是拉取拉取镜像，启动服务。

* 安全，不需要把代码暴露在服务器。

* 镜像同一管理。

# 步骤

## 上传镜像

step1、根据Dockerfile或者 docker-compose.yml文件生成image。

step2、

step1、登陆到镜像仓库

```
$ docker login docker-reg.ifengyu.com:4430
# 输入 用户名和密码
```

step2、

