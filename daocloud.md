## DaoCloud 不支持的功能 {#id-部署复杂的多节点微服务应用-DaoCloud不支持的功能}

Docker Compose运行在本地，而DaoCloud运行在云端。有少量的参数是暂时不支持的。

因此DaoCloud暂时不支持和构建相关的参数。也不支持和本地配置文件有关的参数。包括

* build
* env\_file 
* dockerfile
* extends

* 提交代码，构建完镜像，怎样自动的根据代码中的 docker-compose.yml部署.

我们预期达到的效果：

* 构建 CI、CD流程。

  * 提交代码\(develop分支\)，构建镜像推送到镜像仓库；
  * 拉取代码部署（脚本）到测试服务器；
  * 测试OK，该镜像保留，否则，删除该镜像或者标记该镜像测试失败。
  * 合入 release 分支，得到 release 镜像。
  * 拉取release镜像，预生产测试。
  * 成功，则备份该镜像，作为生产镜像。

* 使用 daocloud，在编排镜像部署时，怎样使用我们自己的 docker-compose.yml文件？

* 怎样做到自动部署到服务器（测试和生产）？

* 因为我们不止一个docker，在构建镜像的时候，目前来看只能 build  Dockerfile，怎样使用我们自己的docker-compose.yml进行 build构建我们的镜像？

---

以上就是我的这些问题，谢谢了。

