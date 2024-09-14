# Лабораторная работа №1. Основы HTTP

## Цель

Целью данной лабораторной работы является изучение основных принципов протокола HTTP.

## Условие

### Задание №1. Анализ HTTP-запросов

1. Зашел на сайт [http://sandbox.usm.md/login](http://sandbox.usm.md/login).
2. Открыл вкладку `Network` в инструментах разработчика браузера.
3. Ввел неверные данные для входа (например, `username: student`, `password: studentpass`).
4. Проанализировал запросы, которые были отправлены на сервер.
5. Ответил на следующие вопросы:
   - Какой метод HTTP был использован для отправки запроса?
   - POST
   - Какие заголовки были отправлены в запросе?
   - Accept, Accept-encoding, Accept-language, Connection, Content-length, Content-Type, Host, Origin, Refer, User-Agent. X-Requested-With
   - Какие параметры были отправлены в запросе?
   - Username и password
   - Какой код состояния был возвращен сервером?
   - 401
   - Какие заголовки были отправлены в ответе?
   - Server, Date, Content-Type, Transfer-Encoding, Connection
7. Повторите шаги 3-5, введя верные данные для входа (`username: admin`, `password: password`).
   - Какой метод HTTP был использован для отправки запроса?
   - POST
   - Какие заголовки были отправлены в запросе?
   - Accept, Accept-encoding, Accept-language, Connection, Content-length, Content-Type, Host, Origin, Refer, User-Agent. X-Requested-With
   - Какие параметры были отправлены в запросе?
   - Username и password
   - Какой код состояния был возвращен сервером?
   - 200
   - Какие заголовки были отправлены в ответе?
   - Server, Date, Content-Type, Transfer-Encoding, Connection

### Задание №2. Составление HTTP-запросов

1. Составьте `GET`-запрос к серверу по адресу `http://sandbox.com`, указав в заголовке `User-Agent` ваше имя и фамилию.
   ```
   curl -H "User-Agent: ChatGPT GPT-4" http://sandbox.com
   ```
2. Составьте `POST`-запрос к серверу по адресу `http://sandbox.com/cars`, указав в теле запроса следующие параметры:
   - `make: Toyota`
   - `model: Corolla`
   - `year: 2020`
    ```
    curl -X POST http://sandbox.com/cars -d "make=Toyota&model=Corolla&year=2020"
    ```
3. Составьте `PUT`-запрос к серверу по адресу `http://sandbox.com/cars/1`, указав в заголовке `User-Agent` ваше имя и фамилию, в заголовке `Content-Type` значение `application/json` и в теле запроса следующие параметры:
   ```json
   {
     "make": "Toyota",
     "model": "Corolla",
     "year": 2021
   }
   ```

   ```
    curl -X PUT http://sandbox.com/cars/1 \
    -H "User-Agent: YourName YourSurname" \
    -H "Content-Type: application/json" \
    -d '{"make": "Toyota", "model": "Corolla", "year": 2021}'

   ```
4. Напишите один из возможных вариантов ответа сервера следующий запрос.
   ```http
   POST /cars HTTP/1.1
   Host: sandbox.com
   Content-Type: application/json
   User-Agent: John Doe
   model=Corolla&make=Toyota&year=2020
   ```

   ```
   HTTP/1.1 400 Bad Request
   Content-Type: application/json
   Content-Length: 75
   Connection: keep-alive
   Date: Sat, 14 Sep 2024 15:45:00 GMT
   Server: nginx/1.24.0

   {
     "error": "Invalid request format",
     "message": "Body must be in valid JSON format."
   }
   ```
   Предположите ситуации, когда сервер может вернуть HTTP-коды состояния 200, 201, 400, 401, 403, 404, 500.

### Задание №3. Дополнительное задание. HTTP_Quest

> [!TIP]
> Пройдите квест отправляя запросы на сервер.

1. Отправьте `POST`-запрос на сервер по адресу `http://sandbox.usm.md/quest`, указав в заголовке User-Agent вашу фамилию и имя (Например `User-Agent: John Doe`).

```http
POST /quest HTTP/1.1
Host: sandbox.usm.md
User-Agent: John Doe
```

**curl**:

```bash
curl -X POST http://sandbox.usm.md/quest -H "User-Agent: John Doe"
```

2. Следуйте инструкциям на сервере, выполняя их по порядку.
3. В конце квеста Вам будет показано секретное слово, которое Вы должны будете предоставить в отчете.

   SECRET `Ki0DHwtpLQwvDhgVDAxbfQ==`
