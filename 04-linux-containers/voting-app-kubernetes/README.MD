
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
docker login

docker build vote/ -t 5d20240/ht-vote:latest
docker build worker/ -t 5d20240/ht-worker:latest
docker build result/ -t 5d20240/ht-result:latest

docker push 5d20240/ht-vote:latest
docker push 5d20240/ht-worker:latest
docker push 5d20240/ht-result:latest
```

