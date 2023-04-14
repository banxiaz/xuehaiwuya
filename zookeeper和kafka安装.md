# 1、安装zookeeper

## 1.1、下载

下载链接：[Apache ZooKeeper](https://zookeeper.apache.org/releases.html)

下载带有bin后缀的文件即可，然后打开powershell，解压文件，移动到指定文件夹。

```powershell
tar -zxvf .\apache-zookeeper-3.7.1-bin.tar.gz
```

## 1.2、更改配置

安装目录下新增两个文件夹，一个命名为 data ，一个命名为 log。

找到解压目录下的 conf 目录，将目录中的 zoo_sample.cfg 文件，复制一份，重命名为 zoo.cfg。

修改 zoo.cfg 配置文件，将默认的 dataDir=/tmp/zookeeper 修改成 zookeeper 安装目录所在的data 文件夹，再增加数据日志的配置。这里配置的路径使用双斜杠，如果是单斜杠，在我们启动服务端的时候就会把我们配置的内容输出到 bin 目录下面。

```ini
dataDir=D:\\Java\\apache-zookeeper-3.7.1-bin\\data
dataLogDir=D:\\Java\\apache-zookeeper-3.7.1-bin\\log
```

## 1.3、查看bin目录

- zkServer.cmd 启动服务端
- zkCli.cmd 启动客户端

查看data和log，配置已生效。

## 1.4、默认端口2181

# 2、安装Kafka

- [kafka日志存储【日志目录】_冬雪是你的博客-CSDN博客_kafka的日志文件在哪](https://blog.csdn.net/m0_45097637/article/details/123648967)

## 2.1、下载

下载链接：http://kafka.apache.org/downloads

然后打开powershell，解压文件，移动到指定文件夹。

```powershell
tar -zxvf .\kafka_2.13-3.2.1
```

## 2.2、更改配置

在根目录下新建log文件夹，修改config文件夹下的server.properties文件，修改

```ini
log.dirs=D:\\Java\\kafka_2.13-3.2.1\\log
```

### 2.3、常用命令

启动kafka之前需要先启动zookeeper，然后进入kafka目录。【cd /d D:\Java\kafka_2.13-3.2.1】

1. 启动kafka

   ```shell
   .\bin\windows\kafka-server-start.bat .\config\server.properties
   ```

2. 创建topic

   ```shell
   cd /d D:\Java\kafka_2.13-3.2.1\bin\windows
   
   kafka-topics.bat --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test
   ```

3. 列出主题

   ```shell
   kafka-topics.bat --list --bootstrap-server localhost:9092
   ```

4. 描述主题

   ```shell
   kafka-topics.bat --describe --bootstrap-server localhost:9092 --topic [Topic Name]
   ```

5. 从头读取消息

   ```shell
   kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic [Topic Name] --from-beginning
   ```

6. 删除主题

   ```shell
   kafka-run-class.bat kafka.admin.TopicCommand --delete --topic [topic_to_delete] --bootstrap-server localhost:9092
   ```

7. 创建producer

   ```shell
   kafka-console-producer.bat --broker-list localhost:9092 --topic test
   ```

8. 创建consumer

   ```shell
   kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic test
   ```

## 2.3、默认端口9092



