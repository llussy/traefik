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