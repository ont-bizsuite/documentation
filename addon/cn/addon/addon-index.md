# addon-index简介

addon-index是addon的汇集及纳管之处，是addon生命周期的起点。一个addon主要分config以及runtime两个部分， config负责前导的配置工作，和runtime的关系一般是一对多，即一个addon可以启动多个实例，不同的实例有不同的配置，而这些配置则由一个config服务提供。目前对于测试网和主网，我们有不同的两个repo，分别是：

1.  测试网： <https://github.com/ont-bizsuite/addon-index>
2.  主网： <https://github.com/ont-bizsuite/addon-index-prod>


# CI/CD架构

config/runtime全部容器化，后端容器平台选择的是kubernetes。
CI/CD依赖github action，在github action中处理addon流程。


# addon configuration meta schema

    {
      "owner": "did:ont:Adg3mfNAbfNwjvtbBSziZnXKKP3HbHNqM5",
      "meta": "",
      "addons": [{
        "domain": "witnessTest001.addon.ont",
        "image": "carltraveler/witness_server:v0",
        "runtimeImage": "carltraveler/witness_runtimev0:v6",
        "official": true,
        "imageProperties": {},
        "tag": "latest",
        "url": "option"
      }],
      "sig": "01c67e328a25ead5c038bfb2337cbef021224fc414204a1090c56298c22ad46939bbbb72fdd28c6f6005b3b681b6b03f19d181f4539a6a43e63be30b110b62a92c"
    }

-   owner: addon的owner
-   meta: meta信息描述
-   addons: addon数组，每一个元素对应一个addon
    -   domain： addon的ons
    -   image: addon config image
    -   runtimeImage: addon runtime image
    -   official: 标记是否是ontology出品，ontology出品为true
    -   tag/url: 暂时未用



# PR审批和addon store部署流程

addon的更新流程。总体上的流程如下：

1.  用户开发addon config/addon runtime，并打包成docker image
2.  用户发起githubPR，一般是先从测试网index开始。
3.  repo的github action处理PR，主要包括签名校验 &#x2013;> 拉起config服务 &#x2013;> 上报config服务地址至addon-server后端
4.  用户通过页面来进行对待启动的runtime相关配置
5.  配置结束addon-server负责拉起runtime服务，并将服务地址返回给客户
6.  客户通过runtime服务地址来进行该addon的请求访问



## 用户发起githubPR

如上文所述，一个addon的生命周期由用户的PR开始。通过在这个repo发起关于addon的PR触发github action来处理此PR。一个典型的配置文件如下：

    {
      "owner": "did:ont:Adg3mfNAbfNwjvtbBSziZnXKKP3HbHNqM5",
      "meta": "",
      "addons": [{
        "domain": "witnessTest001.addon.ont",
        "image": "carltraveler/witness_server:v0",
        "runtimeImage": "carltraveler/witness_runtimev0:v6",
        "official": true,
        "imageProperties": {},
        "tag": "latest",
        "url": "option"
      }],
      "sig": "01c67e328a25ead5c038bfb2337cbef021224fc414204a1090c56298c22ad46939bbbb72fdd28c6f6005b3b681b6b03f19d181f4539a6a43e63be30b110b62a92c"
    }

github action的处理过程是

1.  校验sig是否合法
2.  发起部署image的请求
3.  给到add-server部署好的running image的服务URL




# addon runtime交互协议（Client端）




# addon runtime交互实现校验方法（Client端）




# addon版本管理办法

目前对版本的升级还是走CI/CD流程，我们会对应在容器集群中自动更新对应组件



# addon运行环境切换脚本规范




# addon租户资费管理办法




# 发布addon的流程




# addon-server处理过程

addon-server在收到github action发送过来的请求之后就会将addon信息入库，并访问addon暴露的URL以获得config信息。拿到config信息之后，前端页面就会有该addon的相关显示，并判断是否需要运行runtimeimage，如果有则通知中台
