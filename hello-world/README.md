# KinD ingress example

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml

kubectl wait --namespace ingress-nginx \
  --for=condition=ready pod \
  --selector=app.kubernetes.io/component=controller \
  --timeout=90s

kubectl apply -f https://kind.sigs.k8s.io/examples/ingress/usage.yaml

\@ should output "foo-app"
curl localhost:5180/foo/hostname
\@ should output "bar-app"
curl localhost:5180/bar/hostname