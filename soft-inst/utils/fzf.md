# fzf -- Нечеткий текстовый поиск

> [`<<`](../index.md)

## Установка

```
$ sudo apt install fzf
```

## Использование

### Аргументом к cat, vim, etc.

```
$ vim "$(fzf)"
```

### Поиск в массиве данных

```
$ wget "https://filmsbykris.com/scripts/2020/people.txt"
$ ll|grep people
  -rw-r--r-- 1 eu eu  31M Jun  1 18:35 people.txt
$ cat people.txt|fzf
$ cat people.txt|fzf|cut -f3,5,8
$ cat people.txt|fzf -m|cut -f3,5,8
```

> С опцией `-m` (мультивыбор) можно набрать искомый текст, сделать неск. отметок, удалить текст, набрать иной и опять делать отметки.

### Работа с инфо на сайтах

```
$ wget -qO- "https://filmsbykris.com/scripts/2020/employee.lst"|fzf|cut -d\| -f2
$ wget -qO- "https://filmsbykris.com/scripts/2020/employee.lst"|fzf -m --prompt "Select Crew: "|cut -d\| -f2
```

### Поиск в истории команд оболочки

Следующая команда задаст нечеткий поиск в последних 20 командах:

```
$ history 20|fzf
```
