helm基于[traefik-helm-chart](https://github.com/containous/traefik-helm-chart)

yaml根据helm生成
```bash
# helm list
NAME                  	REVISION	UPDATED                 	STATUS  	CHART                       	APP VERSION	NAMESPACE
traefik-ingress       	1       	Tue Dec 31 17:18:02 2019	DEPLOYED	traefik-2.2.2               	2.1.1      	kube-system

helm get traefik-ingress > Traefik-v2-all.yaml
```