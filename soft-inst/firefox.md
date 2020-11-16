# Firefox

> [`<<`](index.md)


## Установка

```
$ sudo apt-cache search firefox |less
$ sudo apt-get install firefox-esr
```

Устанавливается из-за таких расширений как NoScript, uBlock и, в частности, **Mardown Viewer Webext**, которое довольно удобно для работы с инфой, хранящейся в виде связанных текстовых страничек в формате маркдаун. Однако, если в Винде все работает без нареканий, то для работы данного расширения в Linux требуются некие дополнительные настройки.

## Расширение Mardown Viewer Webext

### Танцы с бубном для работы Mardown Viewer Webext

> [Ресурс](https://github.com/Thiht/markdown-viewer/issues/62#issuecomment-277702230)

В каталоге `.local/share/mime/packages/` создается файл `text-markdown.xml` следующего содержания:

```
<?xml version="1.0"?>
<mime-info xmlns='http://www.freedesktop.org/standards/shared-mime-info'>
  <mime-type type="text/plain">
    <glob pattern="*.md"/>
    <glob pattern="*.mkd"/>
    <glob pattern="*.markdown"/>
  </mime-type>
</mime-info>
```

После этого необходимо обновить базу MIME.

```
$ update-mime-database .local/share/mime
```

### Кастомный CSS

Дополнительным бонусом к даннму расширению является возможность применять для отображения содержимого свои таблицы стилей. В настройках данного расширения есть спец text-area для внесения кастомных стилей.

```
body {
 background-color: #f5f5f5;
}
.markdownRoot {
 background-color: #fff;
 box-sizing: border-box;
 min-width: 200px;
 max-width: 980px;
 margin: 0 auto;
 padding: 45px;
 border: 1px solid #ccc;
}
```
