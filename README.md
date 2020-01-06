helm基于[traefik-helm-chart](https://github.com/containous/traefik-helm-chart)

yaml根据helm生成
```bash
# helm list
NAME                  	REVISION	UPDATED                 	STATUS  	CHART                       	APP VERSION	NAMESPACE
traefik-ingress       	1       	Tue Dec 31 17:18:02 2019	DEPLOYED	traefik-2.2.2               	2.1.1      	kube-system

helm get traefik-ingress > Traefik-v2-all.yaml
```

### Traefik-v2-yaml
```bash
Traefik-v2-all.yaml 包含所有资源,比较多，不建议使用。
建议分开使用，deployment.yaml 和daemonset.yaml 任选其一。

kubectl apply -f crd.yaml
kubectl apply -f rbac.yaml
kubectl apply -f services.yaml
kubectl apply -f deployment.yaml  或 kubectl apply -f  daemonset.yam
kubectl apply -f dashboard.yaml

```


### traefik-migration-tool

```bash
# 迁移工具 https://github.com/containous/traefik-migration-tool
# 使用 kubectl  get ingress --all-namespaces  导出yaml文件,放到input文件夹里
./traefik-migration-tool ingress -i ./input/ -o output/
```

### IngressRouteTCP
[Traefik 2.0 暴露 Redis(TCP) 服务](https://www.qikqiak.com/post/expose-redis-by-traefik2/)
```bash
# traefik 配置中需要加上 - "--entryPoints.redis.address=:6379"
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRouteTCP
metadata:
  name: redis
spec:
  entryPoints:
    - redis
  routes:
  - match: HostSNI(`redis.test.com`)
    services:
    - name: redis
      port: 6379
```