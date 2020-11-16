# Фон рабочего стола

> [`<<`](index.md)  
> [Debian Wiki](https://wiki.debian.org/ru/Fluxbox#A.2BBCQEPgQ9_.2BBEAEMAQxBD4ERwQ1BDMEPg_.2BBEEEQgQ.2BBDsEMA-)

Для установки фона выполнить:

```
$ fbsetbg /путь/к/изображению
```

Также можно добавить или изменить нижеследующую строчку в файле `~/.fluxbox/init` для автоматической установки фона при логине:

```
session.screen0.rootCommand:    fbsetbg /путь/к/изображению
```

> Или:

```
session.screen0.rootCommand:    fbsetbg -l
```

Это установит фоном последнее изображение, которое вы задавали с помощью fbsetbg. 
