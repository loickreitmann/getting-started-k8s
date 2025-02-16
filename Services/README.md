# Services

## Creating a Service Imperatively

```shell
→ kubectl expose pod hello-pod \
--name=hello-svc \
--target-port=8080 \
--type=NodePort

service/hello-svc exposed
```

What does that look like?

```shell
→ kubectl get svc -o wide

NAME         TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE    SELECTOR
hello-svc    NodePort    10.106.213.152   <none>        8080:30712/TCP   113s   app=web
kubernetes   ClusterIP   10.96.0.1        <none>        443/TCP          46d    <none>
```

The web app running on `hello-pod` is now accessible on [http://localhost:30712/](http://localhost:30712/).