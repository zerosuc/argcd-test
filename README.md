## 简介

使用 ArgoCD ApplicationSet 来管理多环境，包括 Git Generator 和 PR Generator。

## 安装 argocd

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

get password:

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

access argocd:

```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

## 基础用法（Application CRD）

```
kubectl apply -f helm/application.yaml
```

## 多环境（代码即环境）

```
kubectl apply -f helm-env/applicationset.yaml
```

## 监听 PR 创建新环境（PR 即环境）

```
kubectl apply -f pr
```
