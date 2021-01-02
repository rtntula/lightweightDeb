# dwm

> [`<<`](../index.md)

## Установка

> [Dwm, Suckless, Simple, yet Powerful](https://www.youtube.com/watch?v=wRh8HQ4ICwE)

###  Установка необходимых библиотек

```
# apt-get install build-essential
# apt install libx11-dev
# apt install libxft-dev
```

### Компиляция

Поскольку Alt используется для переключения раскладки клавиатуры, то для нормальной работы надо преопределить MODKEY с дефолнтого Alt на L-WIN. 

```
# cd /root
# cp -r /home/eu/Downloads/dwm-6.2 .
# cd dwm-6.2
# make clean install
# cp -r /home/eu/Downloads/st-0.8.4 .
# cd st-0.8.4
# make clean install
```

### Запуск

```
$ echo 'exec dwm' >~/.initrc
```
Гасим Х-ы: Ctrl-Alt-BS и вновь запускаем:

```
$ startx
```
