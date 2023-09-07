---
title: Безопасный метод
slug: Glossary/Safe
---

Метод HTTP является **безопасным**, если он не меняет состояние сервера. Другими словами, безопасный метод проводит операции "только чтение" (read-only). Несколько следующих методов HTTP безопасные: {{HTTPMethod("GET")}}, {{HTTPMethod("HEAD")}} или {{HTTPMethod("OPTIONS")}}. Все безопасные методы являются также {{glossary("idempotent", "идемпотентными")}}, как и некоторые другие, но при этом небезопасные, такие как {{HTTPMethod("PUT")}} или {{HTTPMethod("DELETE")}}.

Даже если безопасные методы являются по существу "только для чтения", сервер всё равно может сменить своё состояние: например, он может сохранять статистику. Что существенно, так то, когда клиент вызывает безопасный метод, то он не запрашивает никаких изменений на сервере, и поэтому не создаёт дополнительную нагрузку на сервер. Браузеры могут вызывать безопасные методы, не опасаясь причинить вред серверу: это позволяет им выполнять некоторые действия, например, предварительная загрузка без риска. Поисковые роботы также полагаются на вызовы безопасных методов.

Безопасные методы не обязательно должны обрабатывать только статичные файлы; сервер может генерировать ответ "на-лету", пока скрипт, генерирующий ответ, гарантирует безопасность: он не должен вызывать внешних эффектов, таких как формирование заказов, отправка писем и др..

Правильная реализация безопасного метода - это ответственность **серверного приложения**, потому что сам веб-сервер, будь то Apache, nginx, IIS это соблюсти не сможет. В частности, приложение не должно разрешать изменение состояния сервера запросами {{HTTPMethod("GET")}}.

Вызов _безопасного_ метода, не меняющего состояния сервера:

```
GET /pageX.html HTTP/1.1
```

Вызов _небезопасного_ метода, который может поменять состояние сервера:

```
POST /pageX.html HTTP/1.1
```

Вызов идемпотентного, но небезопасного метода:

```
DELETE /idX/delete HTTP/1.1
```

## Материалы для изучения

### Общие

- Определение [безопасных методов](https://tools.ietf.org/html/rfc7231#section-4.2.1) в спецификации HTTP.

### Технические

- Описание общих безопасных методов: {{HTTPMethod("GET")}}, {{HTTPMethod("HEAD")}}, {{HTTPMethod("OPTIONS")}}
- Описание общих небезопасных методов: {{HTTPMethod("PUT")}}, {{HTTPMethod("DELETE")}}, {{HTTPMethod("POST")}}