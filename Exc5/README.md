# architecture-sprint-7-Exc5

## Последовательность команд для выполнения задания

Выполнить набор команд kubectl для разворачивания сервисов
```bash
kubectl run front-end-app --image=nginx --labels role=front-end --expose --port 80 
kubectl run back-end-api-app --image=nginx --labels role=back-end-api --expose --port 80
kubectl run admin-front-end-app --image=nginx --labels role=admin-front-end --expose --port 80
kubectl run admin-back-end-api-app --image=nginx --labels role=admin-back-end-api --expose --port 80
```

Выполнить команду для наката сетевых политик
```bash
kubectl apply -f .\policies
```