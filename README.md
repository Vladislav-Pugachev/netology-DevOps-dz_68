### Работа с сервис-аккаунтами через утилиту kubectl в установленном minikube

- Как создать сервис-аккаунт?
```
vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ kubectl create serviceaccount netology
serviceaccount/netology created
```

- Как просмотреть список сервис-акаунтов?
```
vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ kubectl get serviceaccounts
NAME       SECRETS   AGE
default    0         160m
netology   0         7s
vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ kubectl get serviceaccount
NAME       SECRETS   AGE
default    0         160m
netology   0         13s
```

- Как получить информацию в формате YAML и/или JSON?

```
vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ kubectl get serviceaccount netology -o yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  creationTimestamp: "2022-11-21T07:24:31Z"
  name: netology
  namespace: default
  resourceVersion: "17202"
  uid: 8a4348c1-a496-400f-b60f-8a44b4420de5
  ```
  ```
  vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ kubectl get serviceaccount default -o json
{
    "apiVersion": "v1",
    "kind": "ServiceAccount",
    "metadata": {
        "creationTimestamp": "2022-11-21T04:44:21Z",
        "name": "default",
        "namespace": "default",
        "resourceVersion": "318",
        "uid": "075013f2-84f0-493f-9913-c6928a3bde81"
    }
}
```
- Как выгрузить сервис-акаунты и сохранить его в файл?

```
vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ kubectl get serviceaccounts -o json > serviceaccounts.json
vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ kubectl get serviceaccount netology -o yaml > netology.yml
vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ ls -l
итого 12
-rw-r--r-- 1 vlad vlad  199 ноя 21 12:27 netology.yml
-rw-r--r-- 1 vlad vlad 1633 ноя 21 12:27 README.md
-rw-r--r-- 1 vlad vlad  868 ноя 21 12:27 serviceaccounts.json
```
- Как удалить сервис-акаунт?

```
vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ kubectl delete serviceaccount netology
serviceaccount "netology" deleted
vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ kubectl get serviceaccounts
NAME      SECRETS   AGE
default   0         163m
```

- Как загрузить сервис-акаунт из файла?
```
vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ kubectl apply -f netology.yml
serviceaccount/netology created
vlad@home:~/Documents/Netology/DevOps/netology-DevOps-dz_68$ kubectl get serviceaccounts
NAME       SECRETS   AGE
default    0         164m
netology   0         2s
```
