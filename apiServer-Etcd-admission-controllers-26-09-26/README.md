# KCD SP

## Create a new local cluster

```bash
k3d cluster create admission-cluster --image rancher/k3s:v1.36.4-k3s1
```

## Create Mutating Admission Policies

```bash
kubectl apply -f binding-mutating-metropolis.yaml
kubectl apply -f mutating-pol-gotham.yaml
```

## Create Mutating Admission Policy Binding

```bash
kubectl apply -f binding-mutating-gotham.yaml
kubectl apply -f binding-mutating-metropolis.yaml
```

## Create Namespaces with labels

```bash
kubectl apply -f ns-batcave.yaml
kubectl apply -f ns-daily-planet.yaml
```

## Create Config Maps to test it

```bash
kubectl apply -f cm-utility-belt.yaml
kubectl apply -f cm-daily-planet-news.yaml
```

## Check for labels

```bash
kubectl get cm --show-labels -A | grep "super.hero"
NAMESPACE         NAME                                                   DATA   AGE     LABELS
batcave           kube-root-ca.crt                                       1      12m   super.hero/team=batman
batcave           utility-belt                                           1      12m   super.hero/team=batman
daily-planet      kube-root-ca.crt                                       1      10m   super.hero/team=superman
daily-planet      last-edition                                           1      10m   super.hero/team=superman
```