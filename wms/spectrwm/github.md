# Установка последней версии из сорцев с github

> [`<<`](index.md)  
> [Patching features into SpectrWM](https://www.youtube.com/watch?v=AhbDpdZ1qWw)

На голой системе:

```
$ sudo apt install git vim build-essentials xorg xserver-org suckless-tools xterm -yy
```

Установка зависимостей для spectrwm

```
$ sudo apt build-dep spectrwm
```

Скачиваем сорцы с github-a:

```
$ mkdir ~/.src; cd .src
$ git clone https://github.com/conformal/spectrwm
```

\[Чтобы создать все пользовательские каты в домашнем каталоге (Документы, Загрузки и т.д.):\]

```
$ cd
[$ xdg-user-dirs-update]
$ git clone https://github.com/linuxdabbler/personal-dot-files dotfiles
$ cd dotfiles
$ chmod +x baraction.sh
$ mv baraction.sh ~/.config/
$ chmod +x bmenu fehbg hush loc louder pmenu quieter vol.sh wal weatherbar.sh weather.sh
$ sudo mv bmenu fehbg hush loc louder pmenu quieter vol.sh wal weatherbar.sh weather.sh /usr/local/bin
```

Теперь разберемся с обоями:

```
$ cd wallpapers
$ sudo mkdir /usr/share/backgrounds
$ sudo mv *.png /usr/share/backgrounds
$ sudo chmod 755 /usr/share/backgrounds
$ sudo chown mike /usr/share/backgrounds   
$ cd /usr/share/backgrounds
$ 
```

`00:18`  
`00:38:37` -- patching
