# Tinder Bot (JavaRush, 2025)

[English](README.md) | [Русский](README.ru.md)

A Telegram bot built during the JavaRush Python marathon. It uses ChatGPT to help write dating profiles, draft messages and practice conversations.

![Tinder Bot](resources/images/avatar_main.jpg)

## Features

- Create a Tinder profile from personal details and interests.
- Suggest opening messages and replies based on a conversation.
- Practice asking someone out through dialogue with preset AI characters, including celebrity-inspired personas.
- Ask ChatGPT general questions from Telegram.

## Bot commands

| Command | Action |
| --- | --- |
| `/start` | Open the main menu |
| `/profile` | Create a dating profile |
| `/opener` | Draft an opening message |
| `/message` | Suggest a reply or an invitation based on supplied messages |
| `/date` | Practice a conversation with an AI character |
| `/gpt` | Ask ChatGPT a question |

![Opening message example](resources/images/opener.jpg)

## Stack and structure

Python, `python-telegram-bot`, the OpenAI Python client and `python-dotenv`.

| Path | Purpose |
| --- | --- |
| [tinder-bot/main.py](tinder-bot/main.py) | Telegram handlers, conversation modes and bot entry point |
| [tinder-bot/classes/gpt.py](tinder-bot/classes/gpt.py) | ChatGPT client and dialogue history |
| [tinder-bot/classes/util.py](tinder-bot/classes/util.py) | Telegram messages, buttons and resource loading |
| [resources/prompts](resources/prompts) | Prompts for profiles, messages and practice conversations |
| [resources/messages](resources/messages) | Bot interface text |
| [resources/images](resources/images) | Images used by the bot |

## Run locally

Use Python 3, a Telegram bot token from [BotFather](https://t.me/BotFather), and an API token for the JavaRush endpoint configured in [gpt.py](tinder-bot/classes/gpt.py): `https://openai.javarush.com/v1`. The client uses the `gpt-3.5-turbo` model.

```bash
git clone https://github.com/ivan-zamula/tinder-bot-v2.git
cd tinder-bot-v2
python3 -m venv .venv
source .venv/bin/activate
python -m pip install python-telegram-bot openai python-dotenv
cp env.example .env
```

Set both variables in the local `.env` file:

| Variable | Value |
| --- | --- |
| `OPEN_API_TOKEN` | API token accepted by the configured JavaRush endpoint |
| `TELEGRAM_TOKEN` | Telegram bot token |

Start the bot from the `tinder-bot` directory so the resource paths resolve correctly:

```bash
cd tinder-bot
python main.py
```

Open your bot in Telegram and send `/start`. Keep the real `.env` file local; [env.example](env.example) contains only the variable names.
