# OTDEL — full bot + Mini App

## Что здесь уже сделано

- Mini App и Telegram-бот работают из одного Python-проекта.
- Telegram `initData` проверяется на сервере.
- ID пользователя берётся из подписанных данных Telegram, а не из `?chats=...`.
- Пользователь видит только свои подключённые чаты.
- Действия в API дополнительно проверяют владельца чата.
- Доступ к Mini App закрыт без активной аренды.
- Главный владелец задаётся через `MASTER_OWNER_ID` и может создавать коды аренды.
- `/rent` активирует код аренды.
- Сроки аренды: 30 / 90 / 365 дней.
- Добавление бота в группу сохраняет чат только если у владельца есть активная аренда.
- Модерация: mute/unmute, ban/unban, warn/unwarn, freeze/unfreeze.
- Events: 777, перебив, угадай цифры.
- Магазин Telegram Stars с реальным invoice через XTR.
- Hero использует `welcome.jpg`, то есть присланную картинку Welcome OTDEL.
- Вместо обычных emoji в интерфейсе используются SVG-иконки.

## ВАЖНО

Токен бота из старого сообщения уже засвечен. Перед запуском обязательно отзови его через @BotFather и создай новый.

## Запуск

```bash
pip install -r requirements.txt
```

Linux / Render / Railway:
```bash
export BOT_TOKEN="НОВЫЙ_ТОКЕН"
export WEBAPP_URL="https://ТВОЙ_HTTPS_ДОМЕН"
export MASTER_OWNER_ID="ТВОЙ_TELEGRAM_ID"
python bot.py
```

Windows:
```bat
set BOT_TOKEN=НОВЫЙ_ТОКЕН
set WEBAPP_URL=https://ТВОЙ_HTTPS_ДОМЕН
set MASTER_OWNER_ID=ТВОЙ_TELEGRAM_ID
python bot.py
```

Приложение слушает `0.0.0.0:8080` по умолчанию.

## Telegram Mini App

В `WEBAPP_URL` должен быть именно публичный HTTPS-адрес этого приложения.

После запуска:
1. Напиши боту `/start`.
2. Открой OTDEL.
3. Добавь бота администратором в группу.
4. Создатель группы должен иметь активную аренду.
5. Группа появится в `Chats`.

## Аренда

Главный владелец:
```text
/rent
```

Выбери 30 / 90 / 365 дней. Бот выдаст код.

Клиент:
```text
/rent XXXXXXXX
```

После активации:
```text
/start
```

и появится кнопка OTDEL.

## Переменные

Скопируй `.env.example` в свои переменные окружения. Не клади настоящий BOT_TOKEN в HTML/JS.
