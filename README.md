# Найстрока сервера

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
