# wallet-rpc

#### 项目介绍
支持各个币种的RPC,RPC的部署及测试都需要有相关钱包节点的支撑
(缺失jar包在jar文件夹中)


####
模块说明


1.bitcoin

* BTC币种RPC


2.erc-token

* 基于以太坊的token
* 部署时，eth模块必须先部署
* 如果有多个token，修改配置文件中的coin.name，coin.unit再部署一个

3.eth

* 以太坊相关RPC

4.eth-support

* 对以太坊及其token提供支持

5.rpc-common

* 公共模块

6.usdt

* usdt币种RPC

7.wallet-mbg

* mybatis相关

## 修改服务配置文件
请根据服务实际部署情况修改以下配置。配置文件位置如下，如果配置文件中没有某一项配置，说明该模块未使用到该项功能，无需添加：

```
各个模块/src/main/resources/dev/application.properties
```

mysql数据库:

```
spring.datasource.**
```

reids

```
redis.**
```

mongodb(主要存储K线图相关数据)

```
spring.data.mongodb.uri
```

kafka

```
spring.kafka.bootstrap-servers
```

### 服务启动
 1. maven构建打包服务

    ```
    cd /项目路径/framework
    mvn clean package
    ```

 2. 将各个模块target文件夹下的XX.jar上传到自己的服务器

 3. 先启动cloud模块，再启动bitcoin

 4. 启动服务

    例：

    ```
    nohup  java  -jar  /自己的jar包路径/cloud.jar  >/dev/null 2>&1 &
    ```