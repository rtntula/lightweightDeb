
# Ungoogled-Chromium

> [`<<`](index.md)

На поверку оказался гораздо легче мозиллы. Следующие команды для **Debian Buster**.

> [Ресурс](https://github.com/ungoogled-software/ungoogled-chromium-debian)

```
$ sudo apt-get install curl gpg
$ echo 'deb http://download.opensuse.org/repositories/home:/ungoogled_chromium/Debian_Buster/ /' | sudo tee /etc/apt/sources.list.d/home-ungoogled_chromium.list > /dev/null
$ curl -s 'https://download.opensuse.org/repositories/home:/ungoogled_chromium/Debian_Buster/Release.key' | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/home-ungoogled_chromium.gpg > /dev/null
$ sudo apt update
$ sudo apt install -y ungoogled-chromium
```
