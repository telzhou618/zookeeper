# zookeeper 源码研究

## 启动配置
1. 下载源码，选择分支branch 3.7
2. 复制 conf/zoo_sample.cfg 到 /conf/zoo.cfg
3. 复制 conf/log4j.properties 到 zookeeper-server 模块的 resources 目录
4. 在zookeeper-server模块的org.apache.zookeeper包下创建version包，创建类Info，内容如下
```java
// Info.java
public interface Info {
    int MAJOR = 1;
    int MINOR = 0;
    int MICRO = 0;
    String QUALIFIER = null;
    int REVISION = -1; //@deprecated, please use REVISION_HASH
    String REVISION_HASH = "1";
    String BUILD_DATE = "2021-09-21";
}
```
5. 启动zk服务端: org.apache.zookeeper.server.quorum.QuorumPeerMain#main(), 参数为zoo.conf配置文件所在位置

![image-20210921153546339](https://raw.githubusercontent.com/telzhou618/images/main/img01/image-20210921153546339.png)

5. 启动zk客户端: org.apache.zookeeper.ZooKeeperMain#main(), 参数为 -server localhost:2181

![image-20210921153619005](https://raw.githubusercontent.com/telzhou618/images/main/img01/image-20210921153619005.png)

6. 在 zk 客户端执行几个测试命令验证，OK

![image-20210921153802642](https://raw.githubusercontent.com/telzhou618/images/main/img01/image-20210921153802642.png)

