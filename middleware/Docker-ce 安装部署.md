# Docker-ce 安装部署

## 部署环境
CentOS

## 部署命令

### 安装yum扩展功能
`
yum install -y yum-utils
`

### 添加软件源
`
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
`

### 安装docker-ce
`
yum install docker-ce
`

### 启动docker
`
systemctl start docker
`

### 验证docker
`
docker
`