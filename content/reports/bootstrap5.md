---
title: "Интеграция Bootstrap 5 с Luxon. Этап 2"
date: 2026-04-26
draft: false
---

## Задание

Создать страницу с Bootstrap 5 и Luxon, где:
- 3 колонки (2-8-2)
- Красная большая кнопка на всю ширину центральной колонки с текстом «Показать время»
- При нажатии — модальное окно
- В заголовке окна — имя и фамилия студента
- В теле окна — текущая дата и время через Luxon
- Закрытие через крестик или кнопку «Закрыть»

## Результат

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/bootstrap-luxon-modal.png" alt="Часы1" width="800">

<img src="https://raw.githubusercontent.com/DariaE8/hugo-portfolio/main/static/images/bootstrap-luxon-modal1.png" alt="Часы2" width="800">

## Код страницы

```html
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bootstrap + Luxon</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        body {
            background-color: #f5f5f5;
            min-height: 100vh;
            display: flex;
            align-items: center;
        }
        .btn-danger {
            width: 100%;
            padding: 15px 0;
            font-size: 1.5rem;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="row">
            <div class="col-2"></div>
            <div class="col-8 text-center">
                <button type="button" class="btn btn-danger" data-bs-toggle="modal" data-bs-target="#timeModal">
                    Показать время
                </button>
            </div>
            <div class="col-2"></div>
        </div>
    </div>

    <div class="modal fade" id="timeModal" tabindex="-1" aria-labelledby="timeModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="timeModalLabel">Ежелева Дарья</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Закрыть"></button>
                </div>
                <div class="modal-body text-center">
                    <h3 id="currentTime"></h3>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Закрыть</button>
                </div>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/luxon@3.4.4/build/global/luxon.min.js"></script>
    <script>
        const timeModal = document.getElementById('timeModal');
        timeModal.addEventListener('show.bs.modal', function () {
            const now = luxon.DateTime.now().setLocale('ru');
            const formattedTime = now.toFormat('dd.MM.yyyy HH:mm:ss');
            document.getElementById('currentTime').innerText = formattedTime;
        });
    </script>
</body>
</html>