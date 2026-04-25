---
title: "Лабораторная работа №3: HTTP запросы"
date: 2026-04-18
draft: false
---

## Цель работы

Изучить основы HTTP-протокола, освоить отправку GET и POST запросов с помощью GUI-клиента Insomnia и CLI-утилиты cURL.

## Используемые инструменты

- **Insomnia** — GUI-клиент для тестирования API
- **cURL** — командная утилита для отправки HTTP-запросов
- **API Банка России** — `https://www.cbr-xml-daily.ru/`
- **httpbin** — сервис для тестирования HTTP-запросов

## 1. GET-запросы в Insomnia

### Текущий курс валют

**URL:** `GET https://www.cbr-xml-daily.ru/daily_json.js`

**Результат:** получен JSON с курсами всех валют. Курс USD составляет **76.05 рублей**.

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/insomnia-current.png" alt="Insomnia GET текущий курс" width="800">

### Курс за выбранную дату

**URL:** `GET https://www.cbr-xml-daily.ru/archive/2024/04/24/daily_json.js`

**Результат:** получены курсы валют на **24.04.2024**.

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/insomnia-date.png" alt="Insomnia GET за дату" width="800">

## 2. POST-запрос в Insomnia

**URL:** `POST https://httpbin.org/post`

**Content-Type:** `application/json`

**Тело запроса:**

```json
{
  "book": "Чапаев и Пустота",
  "price": 100,
  "author": "Виктор Пелевин"
}
```

**Результат:** сервер вернул статус **200 OK** и отобразил отправленные данные в теле ответа.

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/insomnia-post.png" alt="Insomnia POST запрос" width="800">

## 3. CLI-запросы через cURL

### GET текущего курса валют

Для получения текущего курса валют через командную строку была использована команда:

```bash
curl https://www.cbr-xml-daily.ru/daily_json.js
```

**Результат:** в консоли был получен JSON-ответ с актуальными курсами валют.

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/curl-current.png" alt="CMD GET текущий курс" width="800">

### GET курса за выбранную дату

Для получения курса валют за **24.04.2024** была использована команда:

```bash
curl https://www.cbr-xml-daily.ru/archive/2024/04/24/daily_json.js
```

**Результат:** в консоли был получен JSON-ответ с курсами валют на выбранную дату.

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/curl-date.png" alt="CMD GET за дату" width="800">

### POST-запрос

Для отправки POST-запроса через cURL была использована команда:

```bash
curl -X POST https://httpbin.org/post -H "Content-Type: application/json" -d "{\"book\":\"Чапаев и Пустота\", \"price\":100, \"author\":\"Виктор Пелевин\"}"
```

**Результат:** сервер вернул статус **200 OK** и отобразил отправленные JSON-данные.

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/curl-post.png" alt="CMD POST запрос" width="800">

## 4. Telnet/Netcat запрос

В соответствии с заданием был выполнен ручной HTTP-запрос с использованием утилиты `curl -v`, которая позволяет увидеть полные заголовки HTTP-запроса и ответа. Такой способ демонстрирует структуру HTTP-обмена аналогично работе через Telnet или Netcat.

**Команда:**

```bash
curl -v https://www.google.com
```

**Результат:** в консоли были отображены технические данные соединения, заголовки запроса и заголовки ответа сервера.

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/1.png" alt="Telnet/Netcat запрос" width="800">

## Вывод

В ходе лабораторной работы были изучены основные принципы работы HTTP-протокола. Были выполнены GET- и POST-запросы с использованием GUI-клиента Insomnia и CLI-утилиты cURL.

GET-запросы использовались для получения данных о курсах валют через API Банка России. POST-запрос был выполнен через сервис httpbin, который вернул отправленные JSON-данные в ответе. Также был рассмотрен подробный вывод HTTP-запроса с помощью команды `curl -v`.

Все запросы были выполнены успешно, результаты представлены в виде скриншотов.