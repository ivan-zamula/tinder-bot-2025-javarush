# Tinder-бот (JavaRush, 2025)

[English](README.md) | [Русский](README.ru.md)

Telegram-бот, разработанный в рамках марафона JavaRush по Python. Он использует ChatGPT для составления анкет знакомств, подготовки сообщений и тренировки диалогов.

![Tinder-бот](resources/images/avatar_main.jpg)

## Возможности

- Составление Tinder-профиля по личным данным и интересам.
- Подготовка сообщений для знакомства и ответов на основе переписки.
- Тренировка приглашения на свидание в диалоге с заданными ИИ-персонажами, в том числе по образам знаменитостей.
- Общение с ChatGPT прямо в Telegram.

## Команды бота

| Команда | Действие |
| --- | --- |
| `/start` | Открыть главное меню |
| `/profile` | Составить анкету для знакомств |
| `/opener` | Подготовить первое сообщение |
| `/message` | Предложить ответ или приглашение на основе переданных сообщений |
| `/date` | Потренировать диалог с ИИ-персонажем |
| `/gpt` | Задать вопрос ChatGPT |

![Пример сообщения для знакомства](resources/images/opener.jpg)

## Технологии и структура

Python, `python-telegram-bot`, клиент OpenAI для Python и `python-dotenv`.

| Путь | Назначение |
| --- | --- |
| [tinder-bot/main.py](tinder-bot/main.py) | Обработчики Telegram, режимы диалога и точка входа бота |
| [tinder-bot/classes/gpt.py](tinder-bot/classes/gpt.py) | Клиент ChatGPT и история диалога |
| [tinder-bot/classes/util.py](tinder-bot/classes/util.py) | Сообщения, кнопки и загрузка ресурсов Telegram |
| [resources/prompts](resources/prompts) | Промпты для анкет, сообщений и тренировочных диалогов |
| [resources/messages](resources/messages) | Тексты интерфейса бота |
| [resources/images](resources/images) | Изображения бота |

## Локальный запуск

Нужны Python 3, токен Telegram-бота от [BotFather](https://t.me/BotFather) и API-токен для адреса JavaRush, указанного в [gpt.py](tinder-bot/classes/gpt.py): `https://openai.javarush.com/v1`. Клиент использует модель `gpt-3.5-turbo`.

```bash
git clone https://github.com/ivan-zamula/tinder-bot-v2.git
cd tinder-bot-v2
python3 -m venv .venv
source .venv/bin/activate
python -m pip install python-telegram-bot openai python-dotenv
cp env.example .env
```

Заполните обе переменные в локальном `.env`:

| Переменная | Значение |
| --- | --- |
| `OPEN_API_TOKEN` | API-токен, принимаемый настроенным адресом JavaRush |
| `TELEGRAM_TOKEN` | Токен Telegram-бота |

Запускайте бота из папки `tinder-bot`, чтобы относительные пути к ресурсам работали правильно:

```bash
cd tinder-bot
python main.py
```

Откройте своего бота в Telegram и отправьте `/start`. Рабочий `.env` храните локально; [env.example](env.example) содержит только имена переменных.
