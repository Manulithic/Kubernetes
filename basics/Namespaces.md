In simple words, namespaces are nothing but logically isolated environments within your kubernetes cluster that helps you to easily distinguish resources.

TYPES:
------
By default there are 3 namespaces(ns) in your kubernetes cluster:
i) Default: All the resources created insider kubernetes cluster, without mentioning particular namespace, will be created in this ns.
ii) kube-system: All the resources/components required to make cluster work are created in this ns.
iii) kube-public: if you need to create any resource that should be readable by all users must be created in kube-public ns.

DNS WITHIN AND BETWEEN NAMESPACES
---------------------------------

resources within same namespace can refer to other namespace just by the service name. for example: postgresql-db-service

if a resource from a namespace has to communicate or refer to a resource from other namespace, it should happen through FQDN:

```
<service-name>.<namespace-name>.svc.cluster.local

for example:

postgresql-db-service.dev.svc.cluster.local
```


COMMANDS:
---------
i) Command to list all namepaces
```
kubectl get ns
```

ii) To list all the pods in a particular namespace
```
kubectl get pods -n dev
```
#dev here is a namespace name

iii) To create a namespace
```
kubectl create ns dev
```

iv) To list all pods in all namespaces
```
kubectl get pods --all-namespaces
```

v) To delete a namespace
```
kubectl  delete ns <namespace-name>
```

vi) Creating namespace using yaml and limiting resources to your namespace
```
---
apiVersion: v1
kind: Namespace
metadata:
  Name: dev
spec:
  hard:
    pods: "10"
    requests.cpu: "4"
    requests.memory: 5Gi
    limits.cpu: "10"
    limits.memory: 10Gi
...
```
```
kubectl create -f namespace-definition.yaml
```

