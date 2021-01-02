# Поиск в файлах по содержимому

> [`<<`](../index.md)

## find + grep

```
$ find . -name '*.md' -exec grep -Hi --color поиск '{}' \;
```
> С помощью 
