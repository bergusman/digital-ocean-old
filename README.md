# Настройка сервера

https://github.com/bergusman/moneybot/blob/v0.1/docs/do-prepare.md

## Ubuntu

https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04

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
