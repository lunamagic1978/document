# Jenkins docker-compose

## compose文件
```
version: "3"
services:
  jenkins:
    image: jenkins/jenkins:lts
    container_name: jenkins
    restart: always
    ports:
      - '8080:8080'
      - '50000:50000'
    volumes:
      - ./jenkins_home:/var/jenkins_home
```

## 注意点
sudo chown -R 1000 jenkins_home //把当前目录的拥有者赋值给uid 1000