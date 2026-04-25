---
title: "Создание проекта с использованием Webpack"
date: 2026-04-18
draft: false
---

## Цель работы

Научиться использовать Webpack для сборки frontend-проекта, интегрировать библиотеку Luxon для работы с датой и временем, добавить Bootstrap через CDN, а также контейнеризовать приложение с помощью Docker.

## Используемые инструменты

- **Node.js** — среда выполнения JavaScript
- **Webpack** — сборщик модулей
- **Luxon** — библиотека для работы с датой и временем
- **Bootstrap** — CSS-фреймворк (CDN)
- **Docker** — контейнеризация приложения

## 1. Установка и настройка Webpack

### Установка зависимостей

```bash
npm init -y
npm install webpack webpack-cli luxon
```

### Структура проекта

```bash
project/
├── src/
│   └── index.js
├── dist/
│   └── index.html
├── package.json
├── webpack.config.js
└── Dockerfile
```

### Содержимое src/index.js
```javascript
import { DateTime } from 'luxon';

function updateTime() {
  const now = DateTime.now().setLocale('ru');
  const formattedTime = now.toFormat('dd.MM.yyyy HH:mm:ss');
  document.getElementById('app').innerHTML = `
    <div class="container text-center mt-5">
      <h1>Текущее время</h1>
      <div class="display-1 fw-bold text-primary" id="clock">${formattedTime}</div>
    </div>
  `;
}

updateTime();
setInterval(updateTime, 1000);
```

### Содержимое dist/index.html
```html
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Webpack + Luxon</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
    <div id="app"></div>
    <script src="main.js"></script>
</body>
</html>
```

### Конфигурация Webpack (webpack.config.js)
```javascript
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
  mode: 'production',
};
```

## 2. Результат сборки Webpack

### Была выполнена команда:

```bash
npx webpack
```

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/webpack-build.png" alt="Команда" width="800">

## 3. Страница с Bootstrap и крупным выводом времени

### После сборки страница была запущена через:


```bash
npx serve .
```

Результат в браузере (http://localhost:3000):

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/webpack-page.png" alt="Часы" width="800">

## 4. Dockerfile

```Dockerfile
FROM node:20-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npx webpack
EXPOSE 3000
CMD ["npx", "serve", "."]
```
## 5. Запуск приложения через Docker

### Сборка образа
```bash
docker build -t webpack-luxon-app .
```

### Запуск контейнера
```bash
docker run -p 3000:3000 webpack-luxon-app
```

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/webpack-docker.png" alt="Docker" width="800">

### Вывод
В ходе работы были выполнены все поставленные задачи. Проект успешно собирается с помощью Webpack, запускается локально и в Docker-контейнере.