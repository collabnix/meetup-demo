# Demo of Compose on Kubernetes

## Displaying the current context

```
kubectl config current-context
minikube

```

## Verifying Docker Version

```
s-Bay]🚩 >  docker version
Client: Docker Engine - Community
 Version:           18.09.1
 API version:       1.39
 Go version:        go1.10.6
 Git commit:        4c52b90
 Built:             Wed Jan  9 19:33:12 2019
 OS/Arch:           darwin/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          18.09.1
  API version:      1.39 (minimum version 1.12)
  Go version:       go1.10.6
  Git commit:       4c52b90
  Built:            Wed Jan  9 19:41:49 2019
  OS/Arch:          linux/amd64
  Experimental:     true
 Kubernetes:
  Version:          v1.12.4
  StackAPI:         v1beta2
```

## Verifying Minikube Status

```
[Captains-Bay]🚩 >  minikube status
host: Running
kubelet: Running
apiserver: Running
kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100
```

## 

```
pwd
/Users/ajeetraina/meetup_jan_19_demo
```

##

```
[Captains-Bay]🚩 >  helm init --service-account tiller --upgrade
$HELM_HOME has been configured at /Users/ajeetraina/.helm.

Tiller (the Helm server-side component) has been upgraded to the current version.
Happy Helming!
[Captains-Bay]🚩 >  clear
espace compose🚩 >  helm install --name etcd-operator stable/etcd-operator --nam
NAME:   etcd-operator
LAST DEPLOYED: Fri Jan 18 21:00:25 2019
NAMESPACE: compose
STATUS: DEPLOYED

RESOURCES:
==> v1/ServiceAccount
NAME                                               SECRETS  AGE
etcd-operator-etcd-operator-etcd-backup-operator   1        1s
etcd-operator-etcd-operator-etcd-operator          1        1s
etcd-operator-etcd-operator-etcd-restore-operator  1        1s

==> v1beta1/ClusterRole
NAME                                       AGE
etcd-operator-etcd-operator-etcd-operator  1s

==> v1beta1/ClusterRoleBinding
NAME                                               AGE
etcd-operator-etcd-operator-etcd-backup-operator   1s
etcd-operator-etcd-operator-etcd-operator          1s
etcd-operator-etcd-operator-etcd-restore-operator  1s

==> v1/Service
NAME                   TYPE       CLUSTER-IP     EXTERNAL-IP  PORT(S)    AGE
etcd-restore-operator  ClusterIP  10.108.77.217  <none>       19999/TCP  1s

==> v1beta1/Deployment
NAME                                               DESIRED  CURRENT  UP-TO-DATE  AVAILABLE  AGE
etcd-operator-etcd-operator-etcd-backup-operator   1        1        1           0          1s
etcd-operator-etcd-operator-etcd-operator          1        1        1           0          0s
etcd-operator-etcd-operator-etcd-restore-operator  1        1        1           0          0s

==> v1/Pod(related)
NAME                                                             READY  STATUS             RESTARTS  AGE
etcd-operator-etcd-operator-etcd-backup-operator-7978f8bc4hbrk9  0/1    ContainerCreating  0         0s
etcd-operator-etcd-operator-etcd-operator-6c57fff9d5-772w9       0/1    ContainerCreating  0         0s
etcd-operator-etcd-operator-etcd-restore-operator-6d787599pz788  0/1    ContainerCreating  0         0s


NOTES:
1. etcd-operator deployed.
  If you would like to deploy an etcd-cluster set cluster.enabled to true in values.yaml
  Check the etcd-operator logs
    export POD=$(kubectl get pods -l app=etcd-operator-etcd-operator-etcd-operator --namespace compose --output name)
    kubectl logs $POD --namespace=compose
[Captains-Bay]🚩 >  pwd
/Users/ajeetraina/Downloads
[Captains-Bay]🚩 >  cd
[Captains-Bay]🚩 >  cd meetup_jan_19_demo/
[Captains-Bay]🚩 >  kubectl apply -f compose-etcd.yaml
error: unable to recognize "compose-etcd.yaml": no matches for etcd.database.coreos.com/, Kind=EtcdCluster
[Captains-Bay]🚩 >  vi docker-compose.yml
[Captains-Bay]🚩 >  vi compose-etcd.yaml
[Captains-Bay]🚩 >  mv compose-etcd.yaml compose-etcd.yml
[Captains-Bay]🚩 >  mkubectl apply -f compose-etcd.yml
etcdcluster "compose-etcd" created
[Captains-Bay]🚩 >  minikube list
Error: unknown command "list" for "minikube"
Run 'minikube --help' for usage.
[Captains-Bay]🚩 >  minikube service list
|-------------|-----------------------|--------------|
|  NAMESPACE  |         NAME          |     URL      |
|-------------|-----------------------|--------------|
| compose     | compose-api           | No node port |
| compose     | compose-etcd          | No node port |
| compose     | compose-etcd-client   | No node port |
| compose     | etcd-restore-operator | No node port |
| default     | kubernetes            | No node port |
| kube-system | kube-dns              | No node port |
| kube-system | kubernetes-dashboard  | No node port |
| kube-system | tiller-deploy         | No node port |
|-------------|-----------------------|--------------|
[Captains-Bay]🚩 >  kmv compose-etcd.yamlcompose-etcd.yml
```
