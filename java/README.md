## 编译项目

项目是 github 的一个 sprint boot 的项目，地址: `https://github.com/callicoder/spring-boot-mysql-rest-api-tutorial.git`

编译项目
```
cd app
./build.sh
```
构建 docker 镜像
```
cd app
docker build  -t  kuopsme/java-app:1.0 .
docker push kuopsme/java-app:1.0
```

启动
```
kubectl  create  -f java/
```

插入数据
```
NODEPORT=$(kubectl get svc java-spring-boot -o jsonpath='{.spec.ports[0].nodePort}')

curl -X POST  nodeip:${NODEPORT}:8080/api/notes -d '
curl -X POST  nodeip:${NODEPORT}/api/notes -H "Accept: application/json"  -H "Content-Type: application/json; charset=UTF-8" -d '
{
"title": "my first note",
"content": "Hello Spring boot!"
}'
```
访问
```
curl -X GET  nodeip:${NODEPORT}/api/notes
```
