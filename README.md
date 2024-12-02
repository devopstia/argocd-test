## Getting Started
https://argo-cd.readthedocs.io/en/stable/getting_started

```sh
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
kubectl port-forward svc/argocd-server -n argocd 8080:443
argocd admin initial-password -n argocd
https://localhost:8080
argocd login localhost:8080 --username admin --password Q2dFwFsCnm6uNHOy

argocd app create guestbook \
  --repo https://github.com/argoproj/argocd-example-apps.git \
  --path guestbook \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace app
```
```sh
## confluent-operator
argocd app create confluent-operator \
  --repo https://github.com/devopstia/argocd-test.git \
  --path confluent-operator \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace confluent

## cfk
argocd app create cfk \
  --repo https://github.com/devopstia/argocd-test.git \
  --path cfk \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace confluent

## elastic-operator
argocd app create elastic-operator \
  --repo https://github.com/devopstia/argocd-test.git \
  --path elastic-operator \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace elastic-system

## elastic-kibana 
argocd app create elastic-kibana \
  --repo https://github.com/devopstia/argocd-test.git \
  --path elastic-kibana \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace elastic-system

## elastic-kibana 
argocd app create elastic-beats \
  --repo https://github.com/devopstia/argocd-test.git \
  --path elastic-beats \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace elastic-system