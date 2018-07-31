# Настройка сервера

https://github.com/bergusman/moneybot/blob/v0.1/docs/do-prepare.md

## Ubuntu

* https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04
* https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04
* https://www.digitalocean.com/community/tutorials/automating-initial-server-setup-with-ubuntu-18-04

### Новый пользователь

```
adduser vit
```

Права на `sudo`

```
usermod -aG sudo vit
```

Вход под пользователем из другого пользователя

```
su - vit
```

### SSH Ключ

Создаем `.ssh` в домашнем каталоге (`~`)

```
mkdir .ssh
chmod 700 .ssh
```

Добавляем публичный ключ (`id_rsa.pub`)

```
cat .ssh/id_rsa.pub
nano .ssh/authorized_keys
chmod 600 .ssh/authorized_keys
```

### SSHd

## Файрвол UFW

* https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands

## GitHub

Идем в папку `~/.ssh` и копируем приватный ключ на машину

```
scp github_rsa vit@159.65.92.236:~/.ssh/github_rsa
```

Добавляем в конец `~/.profile`

```
eval $(ssh-agent)
ssh-add ~/.ssh/github_rsa
```

## Node.JS

* https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-16-04
* https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-18-04
* https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions

```
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo apt-get install -y build-essential
```

Проверям

```
nodejs -v
npm -v
```

### PM2

* https://pm2.io/


```
sudo npm install -g pm2
```

## Vapor

https://docs.vapor.codes/3.0/install/ubuntu/

Добавлям `Vapor` `Apt` репозиторий

```
eval "$(curl -sL https://apt.vapor.sh)"
```

Устанавливаем `Vapor`

```
sudo apt-get install swift vapor
```

Проверяем `Swift`

```
swift --version
```

## Supervisor

http://supervisord.org/

```
sudo apt-get install -y supervisor
```

Работа с `supervisord`

```
sudo systemctl status supervisor
sudo systemctl start supervisor
sudo systemctl stop supervisor
```

### Vapor

* https://medium.com/@ankitank/deploy-a-basic-vapor-app-with-nginx-and-supervisor-1ef303320726
* https://medium.com/@ahmedraad/how-to-deploy-vapor-app-on-ubuntu-16-04-and-run-it-in-production-eef18f7b4f05
* https://github.com/vapor-community/example

Создайте конфиг для `Vapor` приложения в папке `/etc/supervisor/conf.d`

```
[program:hello]
command=vapor run --env=production
directory=/home/sammy/hello/          # Put correct path here
autorestart=true
user=sammy                            # Put username here
stdout_logfile=/var/log/supervisor/%(program_name)-stdout.log
stderr_logfile=/var/log/supervisor/%(program_name)-stderr.log
```

```
[program:your-app]
command=/path/to/app/.build/release/App serve --ip=127.0.0.1 --port=8080
directory=/path/to/app
user=www-data
stdout_logfile=/var/log/supervisor/%(program_name)-stdout.log
stderr_logfile=/var/log/supervisor/%(program_name)-stderr.log
```

```
[program:vapor-app]
command=/home/myappuser/vapor-app/.build/release/Run serve --env=production
directory=/home/myappuser/vapor-app
user=<username>
stdout_logfile=/var/log/supervisor/%(program_name)-stdout.log
stderr_logfile=/var/log/supervisor/%(program_name)-stderr.log
```

Обновил конфиг и запустил

```
sudo supervisorctl reread
sudo supervisorctl add vapor
sudo supervisorctl start vapor
```

или 

```
sudo supervisorctl update
```

## Nginx

* https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04
* https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-18-04
* https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04-quickstart

```
server {
...
    location /app2 {
        proxy_pass http://localhost:3001;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
...
}
```
