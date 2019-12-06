# 不管firewalld, 设置对外端口

```
firewall-cmd --permanent --zone=public --add-port=8080/tcp
firewall-cmd --reload
```