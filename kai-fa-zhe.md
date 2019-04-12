# 为什么需要自己搭建镜像仓库

* 共有仓库开放，对于企业，不安全。
* 提供商，不友好。

# 意义

* 正规，职责分离，服务器只是拉取拉取镜像，启动服务。

* 安全，不需要把代码暴露在服务器。

* 镜像统一管理，版本管控。

* CI/CD一部分。

# 步骤

## 上传镜像

step1、根据Dockerfile文件生成image，并打上 TAG。

```
$ docker build -t ${DOCK_REG_URL}/${REG_PRJ}/xxx:${IMAGE_TAG} ${DIR} -f ${DOCKFILE}
```

step2、登陆到镜像仓库

```
$ docker login --username ${DOCK_REG_USER} --password ${DOCK_REG_PASSWD} ${DOCK_REG_URL}
```

step3、push 该镜像

```
$ docker push docker-reg.ifengyu.com:4430/cms/test.cms:v1.0
$ docker push ${DOCK_REG_URL}/${REG_PRJ}/xxx:${IMAGE_TAG}
```

## 拉取镜像

step1、登陆到镜像仓库

step2、拉取镜像

```
$ docker pull ${DOCK_REG_URL}/${REG_PRJ}/xxx:${IMAGE_TAG}
```



