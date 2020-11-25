# Настройка WiFi в терминале

> [`<<`](../index.md)  
> [Источник](https://losst.ru/nasrojka-wifi-v-ubuntu)

Для начала решил просканировать эфир на наличие сетей, но сразу получил отлуп.

```
$ sudo iwlist scan |grep -i essid
  Failed to read scan data : Network is down
```

Решаю поднять wifi интерфейс, но тоже неудачно:

```
$ sudo ip link set wlp1s0 up
  Operation not possible due to RF-kill
```

Ставим `rfkill` -- Tool for enabling and disabling wireless devices.

```
$ sudo apt-get install rfkill
```

Запускаем утилиту и видим, что одно из устройств soft-blocked. Дело оказалось в отключенной кнопке wifi.

```
$ rfkill
  ID TYPE      DEVICE              SOFT      HARD
   0 wlan      phy0           unblocked unblocked
   1 wlan      acer-wireless    blocked unblocked
```

Снова сканируем эфир и видим наш роутер:

```
$ sudo iwlist scan |grep -i essid
     ESSID:"MTSRouter-08986C"
     ESSID:"DIR-320NRU"
```

Для WPA2 нам нужно создать запись соответствующую ESSID и ключ доступа, для этого используем пакет программ wpasupplicant.

```
$ sudo wpa_passphrase DIR-320NRU пароль_установленный_на_роутере
```

Получаем сгенерированную запись:

```
network={
ssid="DIR-320NRU"
psk=b8530ddba3a3625b9336be805da8cfb5f2d67d0e776d5ffd2f38b3f11b18a404
}
```

Открываем файл, где хранятся такие записи (если нет -- создаем), и добавляем нашу сгенерированную в него:

```
$ sudo vim /etc/wpa_supplicant/wpa_supplicant.conf
```

Прописываем [статический wifi интерфейс](net-if.md).

Для самого же подключения будем использовать утилиту `wpa_supplicant`. Рассмотрим её синтаксис:

```
$ wpa_supplicant -D драйвер -i интерфейс -c файл_содениения
```

Драйверов, которые задаются опцией -D всего два: это устаревший `wext` и новый драйвер Wifi `nl80211`. Не стоит путать эти драйверы с драйверами устройств. Это универсальная прослойка между этими драйверами и системой. Пробуем сначала второй, а если не работает, то тогда уже первый.

```
$ sudo wpa_supplicant -D wext -i wlp1s0 -c /etc/wpa_supplicant/wpa_supplicant.conf -B
```

Это надо прописать в автозагрузку. Пока не знаю, как правильно. Делаю следующим образом.

```
$ sudo vim /etc/rc.local
  #!bin/sh

  # WiFi
  /sbin/wpa_supplicant -D wext -i wlp1s0 -c /etc/wpa_supplicant/wpa_supplicant.conf -B
$ sudo chmod +x rc.local
$ sudo init 6
```
