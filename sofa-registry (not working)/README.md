# <mark>**NOT WORKING!!**</mark>

---

# SOFARegistry with docker

DockerFile downloaded from: [GitHub - steventong/sofa-registry-docker: alipay sofa-registry by docker](https://github.com/steventong/sofa-registry-docker)

---

# Guide to install sofa registry:

https://www.sofastack.tech/en/projects/sofa-registry/server-quick-start/

## Deployment

SOFARegistry supports two types of deployment modes, which are integrated deployment and independent deployment. This topic describes the simplest integrated single-node deployment. For more information about deployment modes, see the [Deployment topic](https://www.sofastack.tech/en/projects/sofa-registry/deployment).

## Deployment steps

### 1. Download the source code or installation package.

#### Download the source code.

```bash
git clone https://github.com/sofastack/sofa-registry.git
cd sofa-registry
mvn clean package -DskipTests
cp server/distribution/integration/target/registry-integration.tgz <somewhere>
cd <somewhere> && mkdir registry-integration 
tar -zxvf registry-integration.tgz -C registry-integration
cd registry-integration
```

##### If you found the error below when building sofa-registry project, do this:

1. Find all pom.xml in the sofa-registry project

2. Update:
   
   1. maven compiler source to 1.8 (or later)
   
   2. maven compiler target to 1.8 (or later)
   
   3. i.e.
      
      ```xml
      <maven.compiler.source>1.8</maven.compiler.source>
      <maven.compiler.target>1.8</maven.compiler.target>
      ```

#### Download the installation package.

You can download the latest registry-integration-$version.tar.gz package from [Releases](https://github.com/sofastack/sofa-registry/releases).

```bash
mkdir registry-integration 
tar -zxvf registry-integration-$version.tar.gz -C registry-integration
cd registry-integration
```

### 2. Start registry-integration.

#### Linux/Unix/Mac

Startup command: `sh bin/startup.sh`

#### Windows

Double click the startup.bat file under the bin directory.

### 3. Check the running status.

You can access the healthcheck API provided by these three roles, or view logs/registry-startup.log to check the running status.

```bash
# View the healthcheck API of the meta role:
$ curl http://localhost:9615/health/check
{"success":true,"message":"... raftStatus:Leader"}

# View the healthcheck API of the data role:
$ curl http://localhost:9622/health/check
{"success":true,"message":"... status:WORKING"}

# View the healthcheck API of the session role:
$ curl http://localhost:9603/health/check
{"success":true,"message":"..."}
```

----

# SOFARegistry

[![Java CI with Maven](https://github.com/sofastack/sofa-registry/actions/workflows/maven.yml/badge.svg)](https://github.com/sofastack/sofa-registry/actions/workflows/maven.yml)
![license](https://img.shields.io/badge/license-Apache--2.0-green.svg)
[![Coverage Status](https://codecov.io/gh/alipay/sofa-registry/branch/master/graph/badge.svg)](https://codecov.io/gh/sofastack/sofa-registry)
![maven](https://img.shields.io/github/release/sofastack/sofa-registry.svg)

[GitHub - sofastack/sofa-registry: SOFARegistry is a production-level, low-latency, high-availability service registry powered by Ant Financial.](https://github.com/sofastack/sofa-registry)

SOFARegistry 是蚂蚁金服开源的一个生产级、高时效、高可用的服务注册中心。SOFARegistry 最早源自于淘宝的 ConfigServer，十年来，随着蚂蚁金服的业务发展，注册中心架构已经演进至第五代。目前 SOFARegistry 不仅全面服务于蚂蚁金服的自有业务，还随着蚂蚁金融科技服务众多合作伙伴，同时也兼容开源生态。SOFARegistry 采用 AP 架构，支持秒级时效性推送，同时采用分层架构支持无限水平扩展。

## 功能特性

- 支持服务发布与服务订阅
- 支持服务变更时的主动推送
- 丰富的 REST 接口
- 采用分层架构及数据分片，支持海量连接及海量数据
- 支持多副本备份，保证数据高可用
- 基于 [SOFABolt](https://github.com/alipay/sofa-bolt) 通信框架，服务上下线秒级通知
- AP 架构，保证网络分区下的可用性

## 需要

编译需要 JDK 8 及以上、Maven 3.2.5 及以上。

运行需要 JDK 6 及以上，服务端运行需要 JDK 8及以上。

## 文档

- [快速开始](https://www.sofastack.tech/sofa-registry/docs/Server-QuickStart)
- [开发手册](https://www.sofastack.tech/sofa-registry/docs/JAVA-SDK) 
- [运维手册](https://www.sofastack.tech/sofa-registry/docs/Deployment) 
- [发布历史](https://www.sofastack.tech/sofa-registry/docs/ReleaseNotes) 
- [发展路线](https://www.sofastack.tech/sofa-registry/docs/RoadMap) 

## 贡献

[如何参与 SOFARegistry 代码贡献](https://www.sofastack.tech/sofa-registry/docs/Contributing) 

## 致谢

SOFARegistry 最早源于阿里内部的 ConfigServer，感谢毕玄创造了 ConfigServer，使 SOFARegistry 的发展有了良好的基础。同时，部分代码参考了 Netflix 的 [Eureka](https://github.com/Netflix/eureka)，感谢 Netflix 开源了如此优秀框架。

## 开源许可

SOFARPC 基于 [Apache License 2.0](https://github.com/alipay/sofa-rpc/blob/master/LICENSE) 协议，SOFARPC 依赖了一些三方组件，它们的开源协议参见[依赖组件版权说明](http://www.sofastack.tech/sofa-rpc/docs/NOTICE)。
