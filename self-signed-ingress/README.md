
# Aquire a host name for your cluster
In case of KinD just edit the hosts file with 127.0.0.1 kubernetes.docker.internal

# Create a self signed certificate

`openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout example.key -out example.crt -subj "/CN=kubernetes.docker.internal/O=kubernetes.docker.internal" -addext "subjectAltName = DNS:kubernetes.docker.internal"`

# Create a secret with the crt/key pair 

 `kubectl create secret tls hello-app-tls3 --namespace trial --key certs3/example.key --cert certs3/example.crt`

`describe secret hello-app-tls3 --namespace trial`

# apply ingress and deployment app

`kubectl apply -f hello-app.yaml -n=trial`
`kubectl apply -f hello-app-ingress.yaml -n=trial`

# Test
In my KidD cluster 443 is mapped to 51443, -k to tell curl to accept the risk of self-signed cert

curl https://kubernetes.docker.internal:51443/ -k