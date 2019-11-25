# Garfana docker-compose

## compose文件
```
version: '2'
services:
  grafana:
    container_name: grafana
    image: grafana/grafana:6.3.6
    restart: always
    environment:
      GF_AUTH_PROXY_ENABLED: 'true'
      GF_AUTH_ANONYMOUS_ENABLED: 'true'
    ports:
      - 3000:3000
    volumes:
      - /root/grafana/data:/var/lib/grafana
```

## 注意点
挂在出来的目录 data 需要给足权限