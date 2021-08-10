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
$ cp 133.pnd current-wallpaper.png
```

```
$ cd
$ cd dotfiles
$ mv vimrc ~/.vimrc
$ mv Xresources ~/.Xresources
$ cp spectrwm.conf ~/.spectrwm.conf
$ cat bash-alias.txt >> ~/.bashrc

```

```
$ cd .src/spectrwm/linux/
$ make
$ sudo ln -sf ~/.src/spectrwm/linux/spectrwm /usr/local/bin/
$ sudo ln -sf ~/.src/spectrwm/linux/libswmhack.so.0.0 /usr/local/lib/
$ sudo cp spectrwm.desktop /usr/share/xsessions/
```

```
$ cd
$ sudo apt install --no-install-recomends lightdm lightdm-gtk-greeter
$ sudo systemctl enable lightdm
$ sudo reboot
```

```
cd .src/
$ git clone https://github.com/linuxdabbler/suckless
$ cd suckless
$ mv st/ ../
$ cd ..
$ rm -r suckless/
$ cd st
$ make
$ sudo ln -sf ~/.src/st/st /usr/local/bin/
$ cd
$ vim .spectrwm.conf
  program[lock]		= lok
  bind[lock]		= MOD+Shift+Del
```

Let's get Ubuntu Nerd Font

- nerdfonts.com
- dowload -- Ubuntu Nerd Font

```
$ cd Downloads
$ unzip Ubuntu.zip
$ sudo mkdir -p /usr/share/fonts/truetype/nerdfonts/ubuntu
$ sudo mv *.ttf /usr/share/fonts/truetype/nerdfonts/ubuntu/
```

Mod+q to refresh and that's it -- we've got spectrwm installed! Yay!

`00:38:37` -- patching
