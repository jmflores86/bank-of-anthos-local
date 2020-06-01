For new deployments:

1 - Generate RSA key pair secret

openssl genrsa -out jwtRS256.key 4096
openssl rsa -in jwtRS256.key -outform PEM -pubout -out jwtRS256.key.pub
kubectl create secret generic jwt-key --from-file=./jwtRS256.key --from-file=./jwtRS256.key.pub

2 - Deploy frontend on cloud gke

kubectl apply -n bank2 -f frontend

3 - Deploy backend on GKE On-prem

kubectl apply -n bank1 -f backend
