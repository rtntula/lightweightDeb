# Настройка xTerm

> [`<<`](index.md)

Внимание, потребуется также бесплатный шрифт Droid Sans Mono. Создаем каталог `~/.fonts` и распаковываем в него архив со шрифтом.

Для желаемого отображения xTerm необходимо отредактировать файл `~/.Xresources`.

```
!==============================================================================
! XTerm 
!==============================================================================
!Кириллица
XTerm*utf8Title: true
XTerm*faceName: Droid Sans Mono
XTerm*faceSize: 12
xterm*bolfFont: 
xterm*scrollBar:        true
xterm*geometry:         84x38
xterm*eightBitInput:    false
xterm*metaSendsEscape:  true
xterm*colorBDMode:      true
xterm*boldMode:         on
xterm*alwaysBoldMode:   false
xterm*dynamicColors:    on
xterm*colorMode:        on
xterm*saveLines:        10000
xterm*visualBell:       false
 
!==============================================================================
! Цвета 
!==============================================================================
xterm*colorBD:     #e6d51d
xterm*background:  #111111
xterm*foreground:  #b4b4b4
! Чёрный
xterm*color0:      #000000
xterm*color8:      #555753
! Красный
xterm*color1:      #b6212d
xterm*color9:      #ff6565
! Зелёный
xterm*color2:      #4c8d00
xterm*color10:     #6bbe1a
! Жёлтый
xterm*color3:      #ff8040
xterm*color11:     #e6d51d
! Синий
xterm*color4:      #0086d2
xterm*color12:     #00d2ff
! Маджента
xterm*color5:      #963c59
xterm*color13:     #d3649f
! Циановый
xterm*color6:      #105952
xterm*color14:     #177f75
! Белый
xterm*color7:      #cdcaa9
xterm*color15:     #ffffff
```
