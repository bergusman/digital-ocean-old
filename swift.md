# Swift

* https://www.digitalocean.com/community/tutorials/how-to-install-swift-and-vapor-on-ubuntu-16-04
* https://github.com/kylef/swiftenv
* http://dhard.ru/?p=349


## Установка

### Руками

Найти версию на страничке

https://swift.org/download/

Билд `4.1.3` для `Ubuntu 16.04`

https://swift.org/builds/swift-4.1.3-release/ubuntu1604/swift-4.1.3-RELEASE/swift-4.1.3-RELEASE-ubuntu16.04.tar.gz

Загрузить `Swift`

```
wget https://swift.org/builds/swift-4.1.3-release/ubuntu1604/swift-4.1.3-RELEASE/swift-4.1.3-RELEASE-ubuntu16.04.tar.gz
```

Разархивировать

```
tar xzf swift-4.1.3-RELEASE-ubuntu16.04.tar.gz
```

Поставить зависимости

```
sudo apt-get install libpython2.7 clang libicu-dev libcurl3
```

### Swiftenv

https://github.com/kylef/swiftenv
