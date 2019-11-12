# Elasticsearch 虚拟机部署

## 1. 版本

- JDK: 1.8.0
- Elasticsearch: 6.6.2

## 2. 环境
- 操作系统: 
- 配置: 4C8G


## 3. 安装部署
### 安装
#### 安装JDK

`yum -y install java-1.8.0-openjdk`

#### 安装ES

下载文件
`curl -LO https://mirrors.tuna.tsinghua.edu.cn/elasticstack/yum/elastic-6.x/6.6.2/elasticsearch-6.6.2.rpm`

安装RPM
`rpm -ivh elasticsearch-6.6.2.rpm`

### 配置
创建ES数据和日志目录,设置权限

```
mkdir -p /data/es/data /data/es/logs && chown -R elasticsearch.elasticsearch  /data/es
```

这是内存限制, 根据实际资源情况分配,默认配置系统内存的一半大小

```
vim /etc/elasticsearch/jvm.options
-Xms4g
-Xmx4g
```

配置文件 /etc/elasticsearch/elasticsearch.yml

```
cluster.name: es
 
cluster.routing.allocation.disk.threshold_enabled: true
cluster.routing.allocation.disk.watermark.low: 90%
cluster.routing.allocation.disk.watermark.high: 90%
cluster.routing.allocation.node_concurrent_recoveries: 3
cluster.routing.allocation.node_initial_primaries_recoveries: 10
 
node.name: es-01
node.max_local_storage_nodes: 1
 
path.data: /data/es/data
path.logs: /data/es/logs
 
bootstrap.memory_lock: true
 
http.max_content_length: 100mb
http.max_initial_line_length: 4kb
http.max_header_size: 8kb
http.compression: true
 
network.host: 172.16.118.1
 
transport.tcp.connect_timeout: 30s
transport.ping_schedule: 5s
transport.tcp.compress: true

 
action.destructive_requires_name: true
 
indices.recovery.max_bytes_per_sec: 60mb
indices.breaker.fielddata.limit: 50%
indices.fielddata.cache.size: 30%
indices.breaker.request.limit: 50%
indices.breaker.total.limit: 95%
```

### 配置系统参数
内存锁定
编辑limits.conf
`vim /etc/security/limits.conf`
添加内容
```
elasticsearch soft memlock unlimited 
elasticsearch hard memlock unlimited
```

编辑 elasticsearch.servic
`
vim /usr/lib/systemd/system/elasticsearch.service
`
添加内容
```
[Service]
LimitMEMLOCK=infinity
```

## 4. 启动服务

```
systemctl daemon-reload
systemctl restart elasticsearch
systemctl enable  elasticsearch

```

