In simple words, namespaces are nothing but logically isolated environments within your kubernetes cluster that helps you to easily distinguish resources.

TYPES:
------
By default there are 3 namespaces(ns) in your kubernetes cluster:
i) Default: All the resources created insider kubernetes cluster, without mentioning particular namespace, will be created in this ns.
ii) kube-system: All the resources/components required to make cluster work are created in this ns.
iii) kube-public: if you need to create any resource that should be readable by all users must be created in kube-public ns.


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
