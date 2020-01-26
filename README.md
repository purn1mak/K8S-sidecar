# k8s-webhook

1. `cd docker`
2. `docker build . -t localserver`
3. Cut and Paste the root CA from the docker build output `Step 12/13 : RUN cat rootCA.crt | base64 | tr -d '\n'` and replace the value currently in https://github.com/purnimak/k8s-sidecar/blob/master/k8s/hook.yaml#L14
4. `docker login` use your credentials. Create a repository sidecar
5. `docker tag localserver:latest purnimak/private-sidecar:localserver`
6. `docker push purnimak/private-sidecar:localserver`
7. `cd ../k8s`
8. `kubectl create -f deployment.yaml`
9. `kubectl describe deployments webhook-server`
10 `kubectl get pods`
11 `kubectl describe pods webhook-server-58d7fdf878-sgjnr
12 `kubectl get pods`
13. `kubectl create -f service.yaml`
14. `kubectl create -f hook.yaml`
15. `kubectl get mutatingwebhookconfiguration`
15. `kubectl create -f test.yaml`
Describe pod test and see note that it now also includes a new label for foo bar.
