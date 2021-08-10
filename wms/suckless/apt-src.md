# Вариант с apt-src

> [`<<`](index.md)  
> [How to EASILY Install DWM On Ubuntu, Linux Mint or Debian](https://youtu.be/n2T5mtEjBcE)

Данный вариант установки годится для дистрибутивов на основе Debian. Здесь утилита `apt-src` позволяет скачивать сорс-код из официальных репозиториев Debian.

## Установка apt-src

```
# apt update
# apt install apt-src
```

Для этих целей также необходимо раскомментировать репозиторий исходного кода.

```
# vim /etc/apt/sources.list.d/debian.list
  deb-src http://deb.debian.org/debian buster main contrib non-free
```

## Установка dwm

Далее переходим в каталог рута, создаем там кат для сорс-кода приложения и скачиваем его. По ходу также скачиваюся все зависимости необходимые для сборки и запуска приложения.

```
# cd
# mkdir suckless
# cd suckless
# apt-src update
# apt-src install dwm
```

Переходим в каталог с исходным кодом и вносим необходимые изменения.

```
# cd dwm-6.1
# cp conf.def.h conf.def.h.orig
# vim conf.gef.h
  #define MODKEY Mod4Mask
```

Переходим в родительский каталог и компилируем установочный `.deb` пакет, а также устанавливаем его с помощью утилиты `dpkg`.

```
# cd ..
# apt-src build dwm
# dpkg --install ./dwm_6.1-5_i386.deb
```

Далее надо разлогиниться и при повторном входе выбрать `dwm` в качестве оконного менеджера.


## Установка dmenu

```
# cd /root/suckless
# wget https://dl.suckless.org/tools/dmenu-0.8.4.tar.gz
# tar -vxf dmenu-0.8.4.tar.gz
# cd dmenu-0.8.4
# make clean install
```

