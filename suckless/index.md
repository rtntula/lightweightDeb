# dwm

> [`<<`](../index.md)

## Установка

- [Вариант с apt-src](apt-src.md)
- [Вариант с make-install](make-install.md)

## Использование

*Легенда*: ModKey (mk) = **Left-Win** Key

- mk-S-Ret -- запуск терминала
- mk-p -- активация меню
- mk-j / mk-k -- перемешение по окнам в пределах одного тэга
- mk-S-1 (курсор над нужным окном) -- перенести окно нa тег 2
- mk-tagNo -- переход к нумерованнмоу тэгу
- mk-i / mk-d -- увелич / уменьш число окон в мастер фрейме
- mk-Ret -- перенос окна в мастер фрейм (курсор над нужным окном)
- mk-S-c -- убить окно


## Status Bar

Содержимое скрипта `~/.xinitrc`

```
#!/bin/bash

while true
do
	VOL=" Vol. $(amixer get Master | tail -1 | sed 's/.*\[\([0-9]*%\)\].*/\1/')"
	LOCALTIME=$(date +%Y-%m-%d\ %H:%M)
	BAT="Bat. $(acpi -b | awk '{ print $4 }' | tr -d ',')"
	xsetroot -name "$BAT $VOL $LOCALTIME"
	sleep 20s
done
```
