![](../img/otw01.png)

# OverTheWire Bandit Linux Labs

> [`<<`](../index.md)

## Level7

The password for the next level is stored in the file `data.txt` next to the word **millionth**.

```
$ grep -i millionth data.txt
  millionth       cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

## Level6

The password for the next level is stored **somewhere on THE server** and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

```
$ find / -type f -size 33c -user bandit7 -group bandit6
  find: ‘/root’: Permission denied
  find: ‘/home/bandit28-git’: Permission denied
  ...
  /var/lib/dpkg/info/bandit7.password
$ ls -Al /var/lib/dpkg/info/ |grep -E bandit7[.]password --color
  -rw-r----- 1 bandit7 bandit6      33 May  7  2020 bandit7.password
$ cat /var/lib/dpkg/info/bandit7.password
```

## Level5

The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

```
$ find . -type f -size 1033c \! -executable
  ./inhere/maybehere07/.file2
$ ls -Al inhere/maybehere07/ |grep .file2 --color
  -rw-r----- 1 root bandit5 2488 May  7  2020 -file2
  -rw-r----- 1 root bandit5 1033 May  7  2020 .file2
  -rw-r----- 1 root bandit5 9064 May  7  2020 spaces file2
$ ls -Al inhere/maybehere07/ |grep -E [.]file2 --color
  -rw-r----- 1 root bandit5 1033 May  7  2020 .file2
$ file inhere/maybehere07/.file2
  inhere/maybehere07/.file2: ASCII text, with very long lines
$ cat inhere/maybehere07/.file2
```

## Level4

Поиск читабельных текстовых файлов.

```
$ file inhere/*
  inhere/-file01: data
  inhere/-file02: data
  ...
  inhere/-file07: ASCII text
$ cat inhere/-file07
```

## Level3

Работа со скрытыми фалами, типа ".name.txt".

```
$ ls -la inhere/
$ cat inhere/.hidden
```

## Level2

Работа с фалами с пробелами в имени, типа "file name.txt".

```
$ cat spaces\ in\ this\ filename
```

## Level1

Работа с фалами с имененм типа "-file" или даже "-".

```
$ cat ./-
$ rm -- -file
$ rm inhere/-file01
```

> Чтобы перезаписать файл др пользователя добавь **!** - `:w!` или `:x!`. Получается как `chown`, т.к. `группа:владелец` этого файла становятся как у текущего пользователя.

## Level0: Подключение

host: bandit.labs.overthewire.org  
port: 2220  
login: bandit0  
pass: bandit0

```
$ ssh bandit0@bandit.labs.overthewire.org -p 2220

```

### Каталог для записи

Доступ в домашний, `tmp` и `proc` каталоги на запись **закрыт**. Запись возможна в рабочий кат, кот можно создать слеующим образом:

```
$ mktemp -d
$ cd /tmp/tmp.CxihY3bbdb # Мой рабочий кат, созданный командой выше
$ chmod 777 .
```

Дал кату такие права, т.к. на каждом новом уровне будет своя учетка.
