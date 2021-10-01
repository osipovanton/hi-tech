
## Приложение

Устанавливаем git и клонируем репозиторий с приложением

```bash
git clone https://github.com/dockersamples/example-voting-app
```

Создаем директорию в которой будем работать

```bash
mkdir vote-app-k8s
cp -rv example-voting-app/vote vote-app-k8s/vote
cp -rv example-voting-app/worker vote-app-k8s/worker
cp -rv example-voting-app/result vote-app-k8s/result
cd vote-app-k8s
```

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo list
helm show values bitnami/postgresql > pgsql.values.yaml
helm install -f pgsql.values.yaml pgsql bitnami/postgresql
```

```
PostgreSQL can be accessed via port 5432 on the following DNS names from within your cluster:

    pgsql-postgresql.default.svc.cluster.local - Read/Write connection

To get the password for "postgres" run:

    export POSTGRES_PASSWORD=$(kubectl get secret --namespace default pgsql-postgresql -o jsonpath="{.data.postgresql-password}" | base64 --decode)

To connect to your database run the following command:

    kubectl run pgsql-postgresql-client --rm --tty -i --restart='Never' --namespace default --image docker.io/bitnami/postgresql:11.13.0-debian-10-r40 --env="PGPASSWORD=$POSTGRES_PASSWORD" --command -- psql --host pgsql-postgresql -U postgres -d postgres -p 5432

To connect to your database from outside the cluster execute the following commands:

    kubectl port-forward --namespace default svc/pgsql-postgresql 5432:5432 &
    PGPASSWORD="$POSTGRES_PASSWORD" psql --host 127.0.0.1 -U postgres -d postgres -p 5432
```

```bash
helm show values bitnami/redis > redis.values.yaml
helm install -f redis.values.yaml vote bitnami/redis
```

```
1. Run a Redis&trade; pod that you can use as a client:

   kubectl run --namespace default redis-client --restart='Never'  --image docker.io/bitnami/redis:6.2.5-debian-10-r63 --command -- sleep infinity

   Use the following command to attach to the pod:

   kubectl exec --tty -i redis-client \
   --namespace default -- bash

2. Connect using the Redis&trade; CLI:
   redis-cli -h vote-redis-master

To connect to your database from outside the cluster execute the following commands:

    kubectl port-forward --namespace default svc/vote-redis-master 6379:6379 &
    redis-cli -h 127.0.0.1 -p 6379
```

docker login

docker build vote/ -t 5d20240/ht-vote:latest
docker build worker/ -t 5d20240/ht-worker:latest
docker build result/ -t 5d20240/ht-result:latest

docker push 5d20240/ht-vote:latest
docker push 5d20240/ht-worker:latest
docker push 5d20240/ht-result:latest