# Demos for Meetup

## Deleting the Kubernetes Resources

```
[Captains-Bay]🚩 >  kubectl get deploy
NAME      DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
db1       2         2         2            2           5d
web1      2         2         2            2           5d
```

```

[Captains-Bay]🚩 >  kubectl delete deploy db1
deployment "db1" deleted
```

```
[Captains-Bay]🚩 >  kubectl delete deploy web1
deployment "web1" deleted
```

```
[Captains-Bay]🚩 >  kubectl get deploy
No resources found.
```

```
[Captains-Bay]🚩 >  kkubectl delete po,svc --all
service "kubernetes" deleted
```

```
[Captains-Bay]🚩 >  kubectl get deploy
No resources found.
```

```[Captains-Bay]🚩 >  kubectl dget all
NAME             TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
svc/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   10s
```
