
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

## NFS  server

```bash
hostnamectl set-hostname nfs

nmcli connection modify ens192 \
    connection.autoconnect yes \
    ifname ens192 \
    ipv4.method manual \
    ipv4.address 172.30.1.21/24 \
    ipv4.gateway 172.30.1.254 \
    ipv4.dns 172.30.0.1

nmcli connection up ens192
```