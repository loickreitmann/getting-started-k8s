# Pods

## Deploying a Pod

### See the running nodes

```shell
→ kubectl get nodes

NAME             STATUS   ROLES           AGE   VERSION
docker-desktop   Ready    control-plane   45d   v1.30.5
```

### Post pod mamnifest to cluster

```shell
→ kubectl apply -f pod.yml 

pod/hello-pod created
```

### Watching pods

```shell
→ kubectl get pods --watch

NAME        READY   STATUS    RESTARTS       AGE
hello-pod   1/1     Running   16 (21m ago)   45d
```

#### With wider details

```shell
→ kubectl get pods --watch -o wide

NAME        READY   STATUS    RESTARTS       AGE   IP          NODE             NOMINATED NODE   READINESS GATES
hello-pod   1/1     Running   16 (24m ago)   45d   10.1.0.37   docker-desktop   <none>           <none>
```

### Describing a pod

```shell
→ kubectl describe pod hello-pod

Name:             hello-pod
Namespace:        default
Priority:         0
Service Account:  default
Node:             docker-desktop/192.168.65.3
Start Time:       Tue, 31 Dec 2024 17:51:11 -0800
Labels:           app=web
Annotations:      <none>
Status:           Running
IP:               10.1.0.37
IPs:
  IP:  10.1.0.37
Containers:
  web-ctr:
    Container ID:   docker://e570f40e058c8be097012d63abec138eb1ae539ecc137adf1a6754f4f8081ca8
    Image:          loickreitmann/getting-started-k8s:1.0
    Image ID:       docker-pullable://loickreitmann/getting-started-k8s@sha256:ef5f1c3d5a83a2fbac64c9f478675cae3d965bc83be97e80a7d53b0cb117f4af
    Port:           8080/TCP
    Host Port:      0/TCP
    State:          Running
      Started:      Sat, 15 Feb 2025 15:17:24 -0800
    Last State:     Terminated
      Reason:       Error
      Exit Code:    255
      Started:      Sat, 15 Feb 2025 15:05:09 -0800
      Finished:     Sat, 15 Feb 2025 15:16:49 -0800
    Ready:          True
    Restart Count:  16
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-xv24f (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True 
  Initialized                 True 
  Ready                       True 
  ContainersReady             True 
  PodScheduled                True 
Volumes:
  kube-api-access-xv24f:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason          Age   From     Message
  ----    ------          ----  ----     -------
  Normal  SandboxChanged  39m   kubelet  Pod sandbox changed, it will be killed and re-created.
  Normal  Pulled          39m   kubelet  Container image "loickreitmann/getting-started-k8s:1.0" already present on machine
  Normal  Created         39m   kubelet  Created container web-ctr
  Normal  Started         39m   kubelet  Started container web-ctr
  Normal  SandboxChanged  27m   kubelet  Pod sandbox changed, it will be killed and re-created.
  Normal  Pulled          27m   kubelet  Container image "loickreitmann/getting-started-k8s:1.0" already present on machine
  Normal  Created         27m   kubelet  Created container web-ctr
  Normal  Started         27m   kubelet  Started container web-ctr
```

## Multi-Container Pod

```shell
→ kubectl apply -f multi-pod.yml 

pod/nginx created
```

## Deleting a Pod

### By Its Name

```shell
→ kubectl delete pod hello-pod
```

### With Its Pod Definition Files

```shell
→ kubectl delete -f multi-pod.yml 
```
