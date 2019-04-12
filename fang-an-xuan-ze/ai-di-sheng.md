## 关于Harbor

Harbor搭建镜像仓库 + gitlabrunner 方案

Harbor是由VMware中国研发团队负责开发的开源企业级Registry项目，项目地址为`https://github.com/vmware/harbor`，该项目发布5个多月以来，深受用户喜爱，在GitHub获得了1000多个点赞星星和200多个Forks。

Harbor是一个用于存储和分发Docker镜像的企业级Registry服务器，通过添加一些企业必需的功能特性，例如安全、标识和管理等，扩展了开源Docker Distribution，提供了:

* 基于角色的访问控制：用户和存储库是通过“项目”关联，同时用户对同一“项目”下镜像拥有不同访问权限。
* 镜像远程复制（同步）：镜像可以在多个注册表之间复制（同步）。支持负载均衡，高可用性，混合云及多种云的情况。
* 图形管理界面：用户能够快捷浏览、搜索存储库中的镜像并管理项目
* AD/LDAP 集成：Harbor集成企业级AD/LDAP
* 审计日志：镜像存储库的全部操作均可追踪
* RESTful API：RESTful APIs 可用于管理运维，便于与外部系统集成。
* 镜像扫描: 能够自动扫描发现镜像中存在的潜在漏洞。

作为一个企业级私有Registry服务器，Harbor提供了更好的性能和安全,提升用户使用Registry构建和运行环境传输镜像的效率。Harbor支持安装在多个Registry节点的镜像资源复制，镜像全部保存在私有Registry中，确保数据和知识产权在公司内部网络中管控。另外，Harbor也提供了高级的安全特性，诸如用户管理，访问控制和活动审计等。

## 和官方的docker registry的区别

* harbor的功能是在此之上提供用户权限管理、镜像复制等功能，提高使用的registry的效率。

## Harbor的架构 {#harbor的架构}

harbor的整体架构还是很清晰的，下面简单介绍一下，下图展示harbor主要的功能组件和信息流向。

![](/assets/harbor)

主要组件包括proxy，他是一个nginx前端代理，主要是分发前端页面ui访问和镜像上传和下载流量，上图中通过深蓝色先标识；ui提供了一个web管理页面，当然还包括了一个前端页面和后端API，底层使用mysql数据库；registry是镜像仓库，负责存储镜像文件，当镜像上传完毕后通过hook通知ui创建repository，上图通过红色线标识，当然registry的token认证也是通过ui组件完成；adminserver是系统的配置管理中心附带检查存储用量，ui和jobserver启动时候回需要加载adminserver的配置，通过灰色线标识；jobsevice是负责镜像复制工作的，他和registry通信，从一个registry pull镜像然后push到另一个registry，并记录job\_log，上图通过紫色线标识；log是日志汇总组件，通过docker的log-driver把日志汇总到一起，通过浅蓝色线条标识。



