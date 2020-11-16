# Swappiness

> [`<<`](index.md)  

## Посмотреть значение

```
$ sysctl vm.swappiness
```

> или

```
$ cat proc/sys/vm/swappiness
```

Дефолтные значения обычно порядка 60, что вполне подходит для сереверов. Но мы то юзаем ноутбук.

## Установить значение

```
$ sudo vim /etc/sysctl.conf
  vm.swappiness = 10
```
