# SoftMaker FreeOffice

> [`<<`](index.md)  
> [`Источник`](https://www.freeoffice.com/ru/tips-and-tricks-linux)

## Установка

```
$ su -
$ apt update
$ dpkg -i ./softmaker-freeoffice-2018_980-01_i386.deb
$ apt install -f
```

## Настройка автоматических обновлений

Добавление репозитория `https://shop.softmaker.com/repo/apt` для автоматического обновления.

```
$ sudo -s
# /usr/share/freeoffice2018/add_apt_repo.sh
```
