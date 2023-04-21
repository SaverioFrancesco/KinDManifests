
# How TO
## Create KinD
`kind create cluster --config=../kind.config`

## Create ServiceAccount
`kubectl apply -f account.yaml`

## Apply Dashboard
`kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml`

## Apply Ingress NGNIX for KinD
`kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml`

`kubectl wait --namespace ingress-nginx --for=condition=ready pod --selector=app.kubernetes.io/component=controller --timeout=90s`

## Create self Signed
`kubectl create secret tls dashb-tls3 --namespace kubernetes-dashboard --key certs/example.key --cert certs/example.crt`

## Apply Ingress NGNIX for KinD
`kubectl apply -f ingress.yaml`