# 意义

* 正规，职责分离，服务器只是拉取拉取镜像，启动服务。

* 安全，不需要把代码暴露在服务器。

* 镜像统一管理，版本管控。

* CI/CD一部分。

# 步骤

## 上传镜像

step1、根据Dockerfile或者 docker-compose.yml文件生成image。

```
$ docker build -t url/prj/xx:tag dir -f Dockfile
# 或者
# docker-compose build .
```

step2、给响应的镜像打标签。

```
$ docker tag cms_web docker-reg.ifengyu.com:4430/cms/test.cms:v1.0
```

step3、登陆到镜像仓库

```
$ docker login docker-reg.ifengyu.com:4430
# 输入 用户名和密码
```

step4、push 该镜像

```
$ docker push docker-reg.ifengyu.com:4430/cms/test.cms:v1.0
```

## 拉取镜像

step1、登陆到镜像仓库

step2、拉取镜像

```
$ docker pull docker-reg.ifengyu.com:4430/cms/test.cms:v1.0
```



