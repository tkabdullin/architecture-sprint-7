# architecture-sprint-7-Exc4

## Последовательность команд для выполнения задания

Разворачивание namespaces
```bash
kubectl create namespace homeowner-namespace
kubectl create namespace client-namespace
kubectl create namespace homeowner-crm-namespace
```

Создание пользователей
```bash
openssl genrsa -out cluster-admin-user.key 2048
openssl req -new -key cluster-admin-user.key -out cluster-admin-user.csr -subj "/CN=cluster-admin-user"
openssl x509 -req -in ./cluster-admin-user.csr -CA ~/.minikube/ca.crt -CAkey ~/.minikube/ca.key -CAcreateserial -out cluster-admin-user.crt -days 365
kubectl config set-credentials cluster-admin-user --client-certificate=cluster-admin-user.crt --client-key=cluster-admin-user.key

openssl genrsa -out developer-homeowner-user.key 2048
openssl req -new -key developer-homeowner-user.key -out developer-homeowner-user.csr -subj "/CN=developer-homeowner-user"
openssl x509 -req -in ./developer-homeowner-user.csr -CA ~/.minikube/ca.crt -CAkey ~/.minikube/ca.key -CAcreateserial -out developer-homeowner-user.crt -days 365
kubectl config set-credentials developer-homeowner-user --client-certificate=developer-homeowner-user.crt --client-key=developer-homeowner-user.key

openssl genrsa -out devops-engineer-user.key 2048
openssl req -new -key devops-engineer-user.key -out devops-engineer-user.csr -subj "/CN=devops-engine-user"
openssl x509 -req -in ./devops-engine-user.csr -CA ~/.minikube/ca.crt -CAkey ~/.minikube/ca.key -CAcreateserial -out devops-engine-user.crt -days 365
kubectl config set-credentials devops-engine-user --client-certificate=devops-engine-user.crt --client-key=devops-engine-user.key

openssl genrsa -out maintenance-engineer-user.key 2048
openssl req -new -key maintenance-engineer-user.key -out maintenance-engineer-user.csr -subj "/CN=maintenance-engineer-user"
openssl x509 -req -in ./maintenance-engineer-user.csr -CA ~/.minikube/ca.crt -CAkey ~/.minikube/ca.key -CAcreateserial -out maintenance-engineer-user.crt -days 365
kubectl config set-credentials maintenance-engineer-user --client-certificate=maintenance-engineer-user.crt --client-key=maintenance-engineer-user.key

openssl genrsa -out log-reader-user.key 2048
openssl req -new -key log-reader-user.key -out log-reader-user.csr -subj "/CN=log-reader-user"
openssl x509 -req -in ./log-reader-user.csr -CA ~/.minikube/ca.crt -CAkey ~/.minikube/ca.key -CAcreateserial -out log-reader-user.crt -days 365
kubectl config set-credentials log-reader-user --client-certificate=log-reader-user.crt --client-key=log-reader-user.key
```

Создание и применение ролей над пользователями
```bash
kubectl create -f .\roles.yaml
kubectl create -f .\rolesBindings.yaml
```
