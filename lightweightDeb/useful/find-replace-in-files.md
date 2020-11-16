# Поиск и замена в файлах

> [`<<`](../index.md)

Искать рекурсивно в текущем каталоге файлы с расширением `.md`, с текстом `Back`, который нужно заменить на `<<`.

```
$ find . -type f -name '*.md' -exec sed -i -r 's/Back/<</' {} \;
```

#### NB!
No actual change to files is made until `-i` option is specified.
