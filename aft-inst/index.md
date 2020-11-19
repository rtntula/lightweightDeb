# Донастройка системы

> [`<<`](../index.md)

## Установка sudo

Во-первых, необходимо установить sudo, и добавить пользователя в sudoers.

- становимся рутом
- устанавливаем **sudo**
- добавляем пользователя в `sudoers`
  - создаем файл с именем пользователя и прописываем то, что нужно.

> Инфо по sudoers хранится в файле `/etc/sudoers`, в котором есть директива по инклюду файлов из каталога `/etc/sudoers.d/`. Разрешения на этих файлах должны быть **440**.

```
$ su
# apt-get install sudo
# touch /etc/sudoers.d/eu
# vi /etc/sudoers.d/eu
  eu ALL=(ALL) ALL
# chmod 440 /etc/sudoers.d/eu
# exit
$ sudo init 6
```

- Делаем снимок машины.


## Установка флюксбокса

```
$ sudo apt-get install xorg fluxbox xterm
```

Устанавливаем X дисплей-менеджер.

```
$ sudo apt-get install xdm
$ sudo reboot (init 6)
```

- После перезагрузки перед нами графическое окошко авторизации.
- Далее загружается флюксбокс и, вуаля,  полчуаем рабочую среду.


## Снимок системы &mdash; RSYNC

Копия работоспособной системы сохраняется на флешку во избежание пагубных последствий экспериментов и неумелых действий пользователя.

> Перед запуском не забыть очистить кэш браузера!!

```
$ sudo rsync -aAXPv --delete --dry-run --exclude=/dev/* --exclude=/proc/* --exclude=/sys/* --exclude=/tmp/* --exclude=/run/* --exclude=/mnt/* --exclude=/media/* --exclude="swapfile" --exclude="lost+found" //mnt/usb/deb
```

- -a - архивный режим;
- -A - сохранение разрешений
- -X - сохранение расширенных аттрибутов
- -P - показывать проргресс 
- -v - вывод копируемых файлов
- --delete - удалять файлы, кот отсутствуют в оригинале
- --dry-run - прогон с показом копируемых файлов без выполнения операции

### Подготовка флешки

Пример форматирования usb флешки в формате ext4 с меткой BACKUPS

> флешка не должна быть смонтирована !!

```
$ sudo mkfs.ext4 /dev/sdb1 -L 'BACKUPS'
mke2fs 1.44.5 (15-Dec-2018)
/dev/sdb1 contains a vfat file system labelled 'BACKUPS'
Proceed anyway? (y,N) y
Creating filesystem with 3785728 4k blocks and 946560 inodes
Filesystem UUID: c3539c00-356a-447a-ad5b-52624c12a28c
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (16384 blocks): done
Writing superblocks and filesystem accounting information: done  
```

```
$ df -hT /mnt/usb/
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb1      ext4   15G   41M   14G   1% /mnt/usb
eu@deb:~/tuning$
```

## Восстановление swap-а

### Посмтотреть, есть ли своп в системе

```
$ swapon --show
```

> или

```
$ free -h
```

### Создать и активировать файл свопа

```
$ sudo fallocate -l 2G /swapfile
$ sudo chmod 600 /swapfile
$ sudo mkswap /swapfile
$ sudo swapon /swapfile
```

### Прописать своп в fstab

```
$ sudo vim /etc/fstab
	/swapfile none swap defaults 0 0
$ sudo init 6
```

### Поменять размер свопа

```
$ sudo swapoff -a
$ sudo fm -f /swapfile
```

> Повторить операции из раздела Создать с нужным размером свопфайла и ребутимся
