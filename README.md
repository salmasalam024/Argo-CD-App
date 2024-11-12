# install ArgoCD in k8s
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# access ArgoCD UI
kubectl get svc -n argocd

kubectl port-forward svc/argocd-server 8080:443 -n argocd

# get admin passwd
kubectl get secret argocd-initial-admin-secret -n argocd -o yaml

# decode the passwd
ech0 "paswd" | base64 --decode

# apply ardocd file
kubectl apply -f application.yaml
