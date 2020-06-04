# GitLab安装

## 安装gitlab-ce

安装并配置必要的依赖关系

```
yum install -y curl policycoreutils-python openssh-server openssh-clients

systemctl enable sshd

systemctl start sshd

firewall-cmd --permanent --add-service=http

systemctl reload firewalld
```

添加GitLab软件包并且安装

```
curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | bash

sudo EXTERNAL_URL="http://rainbow.yannxia.top" yum install -y gitlab-ce
```