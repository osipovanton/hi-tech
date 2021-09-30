
## Приложение

Устанавливаем git и клонируем репозиторий с приложением

```bash
dnf install -y git
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

