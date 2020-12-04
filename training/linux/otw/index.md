![](img/otw01.PNG)

<span style="color: brown; font-family: Times; font-size: 32px; font-weight: bold;">OverTheWire Bandit Linux Labs</span>

> [`<<`](../index.md)

## Level 13

The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user **bandit14**. For this level, you don’t get the next password, but you get **a private SSH key** that can be used to log into the next level. Note: `localhost` is a hostname that refers to the machine you are working on

```
$ ls -lA |grep priv
  -rw-r----- 1 bandit14 bandit13 1679 May  7  2020 sshkey.private
$ head -n 2 sshkey.private 
  -----BEGIN RSA PRIVATE KEY-----
  MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
$ ssh bandit14@localhost -i sshkey.private
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
  4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
bandit14@bandit:~$ ls -lA
  total 16
  -rw-r--r-- 1 root root  220 May 15  2017 .bash_logout
  -rw-r--r-- 1 root root 3526 May 15  2017 .bashrc
  -rw-r--r-- 1 root root  675 May 15  2017 .profile
  drwxr-xr-x 2 root root 4096 May  7  2020 .ssh
```

## Level12

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.

```
$ mv data.txt data.hex
$ head data.hex
  00000000: 1f8b 0808 0650 b45e 0203 6461 7461 322e  .....P.^..data2.
  00000010: 6269 6e00 013d 02c2 fd42 5a68 3931 4159  bin..=...BZh91AY
$ xxd -r data.hex >data.bin
$ file data.bin 
  data.bin: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
  ...
```

```
$ gzip -lN data.bin
  compressed        uncompressed  ratio uncompressed_name
         606                 573  -0.9% data2.bin
$ gzip -d file.gz  # иногда для обработки файл треб переименования
  ...
$ bzip2 -dk file.bz2  # just to decompress, -k to save the orig compressed file
  bzip2: Can't guess original name for data2.bin -- using data2.bin.out
  ...
$ tar -tvf data4.bin
  -rw-r--r-- root/root     10240 2020-05-07 21:14 data5.bin
$ tar -xf file.tar
  ...
```

```
  ...
$ cat data9.bin
  The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

data.hex|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;
---:|---|---|---|---|---|---|---|--- 
**arch**:|data.bin |data2.bin |data2 |data4.bin |data5.bin |data6.bin |data6 |data8.bin
**type**:|gzip |bzip2 |gzip |tar |tar |bzip2 |tar |gzip
**file**:|data2.bin |data2 |data4.bin |data5.bin |data6.bin |data6 |data8.bin |**data9.bin**

## Level11

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

```
$ cat data.txt
  Gur cnffjbeq vf 5Gr8L4qetPEsPk8htqjhRK8XSP6x2RHh
$ cat data.txt | tr a-zA-Z n-za-mN-ZA-M
  The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

Rotated by 13 positions: a->n, b->o ... z->m.

## Level10

The password for the next level is stored in the file `data.txt`, which contains **base64** encoded data

```
$ cat data.txt
  VGhlIHBhc3N3b3JkIGlzIElGdWt3S0dzRlc4TU9xM0lSRnFyeEUxaHhUTkViVVBSCg==
$ base64 -di data.txt
  The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

Утилита `base64` кодирует или декодирует Файл или стандартный ввод на стандартный
вывод в/из base64.

## Level9

The password for the next level is stored in the file `data.txt` in one of the few human-readable strings, preceded by several ‘**=**’ characters.

```
$ file data.txt
  data.txt: data
$ strings data.txt |grep -E '= ' --color
  ========== the*2i"4
  ========== password
  Z)========== is
  &========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```

Утилита `srtings` извлекает печатаемые символы из файла с данными.

## Level8

The password for the next level is stored in the file `data.txt` and is the only line of text that **occurs only once**.

```
$ sort data.txt >/tmp/tmp.CxihY3bbdb/sorted.txt
$ cd /tmp/tmp.CxihY3bbdb
$ uniq -c sorted.txt |grep -E '1 '
  1 UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

или в одно касание

```
bandit8@bandit:~$ sort data.txt |uniq -c |grep -E '1 '
  1 UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

С ключем `-c` утилита `uniq` подсчитывает число идущих подряд повторяющихся строк (почему и нужна **сортировка**). Далее отображаются только уникальные строки с указанинм числа повторов перед каждой строкой через пробел. Т.о. нужная нам строчка будет с символом 1, за кот следует пробел.

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
