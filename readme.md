
# Installtion 

Add helm repo for Bitnami
first of all we must add helm repo;
```
helm repo add bitnami https://charts.bitnami.com/bitnami
```

Then install Minio
`helm install -n zk-core zk-minio bitnami/minio -f values.yaml -f zekoder.values.yaml`

Root User: admin or run `echo $(kubectl get secret --namespace zk-core zk-minio -o jsonpath="{.data.root-user}" | base64 -d)`

## To get root password
`echo $(kubectl get secret --namespace "zk-core" zk-minio -o jsonpath="{.data.root-password}" | base64 -d)`

# Upgrade

`helm upgrade -n minio newspaper-minio bitnami/minio -f values.yaml -f newspaper.dev.values.dev.yaml --set auth.rootPassword=xfja3cWXd2`

You must provide your current passwords when upgrading the release


Note
====
API ingress will always fail due to incoreect livenessProbe configuration for API Ingress (manual fix required till bitnami chart is fixed)