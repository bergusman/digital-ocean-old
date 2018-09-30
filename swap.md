# Swap

https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-18-04

### Проверка свопа

Посмотреть текущий настроенный своп:

```
$ sudo swapon --show
```

Или так:

```
$ free -h
```

Посмотреть используемое место на диске:

```
$ df -h
```

### Создание

Создаем файл заданого размера в корне:

```
$ sudo fallocate -l 1G /swapfile
```

Проверяем:

```
$ ls -lh /swapfile
```

Делаем своп файл доступным только `root`:

```
$ sudo chmod 600 /swapfile
```

Помечаем файл как своп:

```
$ sudo mkswap /swapfile
```

Включаем своп:

```
$ sudo swapon /swapfile
```

Проверяем:

```
$ sudo swapon --show
```

или

```
$ free -h
```

### Сохраняем свов между перезагрузкой


