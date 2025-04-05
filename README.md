# fitness-miniapp
import os
from pathlib import Path
html_code = """<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Фитнес Кабинет</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="https://telegram.org/js/telegram-web-app.js"></script>
  <style>
    body {
      font-family: sans-serif;
      padding: 20px;
      background: #f2f2f2;
    }
    h1 { text-align: center; }
    .card {
      background: #fff;
      border-radius: 12px;
      padding: 20px;
      margin-bottom: 20px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }
    button {
      width: 100%;
      padding: 12px;
      border: none;
      border-radius: 8px;
      background: #30a7d7;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background: #2593c7;
    }
  </style>
</head>
<body>
  <h1>Добро пожаловать!</h1>

  <div class="card">
    <h2>📅 Расписание</h2>
    <p>Пн, Ср, Пт — 18:00 | Силовая тренировка<br>Вт, Чт — 19:00 | Кардио</p>
    <button onclick="onSignUp()">Записаться</button>
  </div>

  <div class="card">
    <h2>💳 Абонемент</h2>
    <p>Текущий: 8 занятий / 1 месяц<br>Осталось: 3 тренировки</p>
    <button onclick="onBuy()">Купить абонемент</button>
  </div>

  <div class="card">
    <h2>📲 Связь с тренером</h2>
    <p>Вы можете задать вопрос или получить рекомендации</p>
    <button onclick="onChat()">Написать</button>
  </div>

  <script>
    const tg = window.Telegram.WebApp;
    tg.ready();

    function onSignUp() {
      tg.sendData(JSON.stringify({action: 'signup'}));
      tg.close();
    }

    function onBuy() {
      tg.sendData(JSON.stringify({action: 'buy'}));
      tg.close();
    }

    function onChat() {
      tg.sendData(JSON.stringify({action: 'chat'}));
      tg.close();
    }
  </script>
</body>
</html>"""

# Сохраняем файл
project_dir = Path("/mnt/data/fitness-miniapp")
project_dir.mkdir(parents=True, exist_ok=True)
html_file = project_dir / "index.html"
html_file.write_text(html_code)

html_file.name
