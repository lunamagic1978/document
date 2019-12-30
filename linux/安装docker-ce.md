# 安装docker-ce

```
yum install -y -q yum-utils
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum makecache
yum install -y docker-ce
```