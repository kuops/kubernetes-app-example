## 构建 php-app 镜像

```
cd app
docker build -t kuopsme/php-app:1.0  .
docker push kuopsme/php-app:1.0
```
##  部署 php-app

```
kubectl  create  -f php/
```

## 访问

```
curl nodeip:nodeport/info.php
curl nodeip:nodeport/test.php
```
