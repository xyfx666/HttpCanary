### Блокировка Mime-Type

Плагин экранирования Mime-Type может экранировать запрос или ответ указанного сетевого протокола HTTP. Пользователям необходимо настроить в /HttpCanary/plugins/MimeTypeBlock/req-mimes.txt или res-mimes.txt, первый - для блокировки данных запроса, а второй - для блокировки данных ответа. Файл будет создан автоматически при установке подключаемого модуля. Пользователю нужно только отредактировать и ввести указанный Mime-Type. **v3.1.5 версии** и более поздние версии поддерживают использование * и? Подстановочных знаков.

Возьмем в качестве примера req-mimes.txt, формат настроенного Mime-Type следующий:

```
# Блокировать все запросы изображений (использовать подстановочный знак *)
образ/*

# Блокировать запрос JSON
приложение / json
```

Ниже приведены два конкретных примера req-mimes.txt и res-mimes.txt:

[Образец файла](https://raw.githubusercontent.com/MegatronKing/HttpCanary/master/plugins/MimeTypeBlock/req-mimes.txt)

[Образец файла](https://raw.githubusercontent.com/MegatronKing/HttpCanary/master/plugins/MimeTypeBlock/res-mimes.txt)

Для типа Mime-Type вы можете обратиться к:
[Официальный список MimeType](https://www.iana.org/assignments/media-types/media-types.xhtml)
