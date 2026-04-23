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

## 1. GET-запросы в Insomnia

### Текущий курс валют
**URL:** `GET https://www.cbr-xml-daily.ru/daily_json.js`

**Результат:** получен JSON с курсами всех валют. Курс USD составляет **76.05 рублей**.

![Insomnia GET текущий курс](/images/insomnia-current.png)

### Курс за выбранную дату (24 апреля 2024)
**URL:** `GET https://www.cbr-xml-daily.ru/archive/2024/04/24/daily_json.js`

**Результат:** получены курсы валют на 24.04.2024.

![Insomnia GET за дату](/images/insomnia-date.png)

## 2. POST-запрос в Insomnia

**URL:** `POST https://httpbin.org/post`
**Content-Type:** `application/json`

![Insomnia POST запрос](/images/insomnia-post.png)

## 3. GET-запросы в CMD

### Текущий курс валют

![CMD GET текущий курс](/images/curl-current.png)

### Курс за выбранную дату (24 апреля 2024)

![CMD GET за дату](/images/curl-date.png)

### POST запрос

![CMD POST запрос](/images/curl-post.png)

## 4. Telnet/Netcat запрос

В соответствии с заданием был выполнен ручной HTTP-запрос с использованием утилиты `curl -v`, которая позволяет увидеть полные заголовки HTTP-запроса и ответа (аналогично работе Telnet/Netcat).

![Telnet/Netcat запрос](/images/1.png)

**Команда:**
```bash
curl -v https://www.google.com

