# Getting Started on Okteto with Java (Maven)

This example shows how to leverage [Okteto](https://github.com/okteto/okteto) to develop a Java Sample App directly in Kubernetes. The Java Sample App is deployed using raw Kubernetes manifests.

This is the application used for the [How to Develop and Debug Java Applications in Kubernetes](https://okteto.com/blog/how-to-develop-java-apps-in-kubernetes/) blog post.

## How to

```
docker build -t jabrena/okteto-demo .
docker push jabrena/okteto-demo:latest
export KUBECONFIG=$HOME/Downloads/okteto-kube.config:${KUBECONFIG:-$HOME/.kube/config}
okteto up
kubectl get all --namespace=jabrena
kubectl create -f k8s.yml
kubectl delete deploy/hello-world-jab svc/hello-world-jab
kubectl get pods
```