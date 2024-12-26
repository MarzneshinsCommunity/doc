---
title: Notifications  
weight: 5  
---

To receive notifications through a Telegram bot, you can follow the steps below:

{{% steps %}}

### 1. Edit the `.env` file

First, open the `.env` configuration file using the `nano` editor:

```bash
nano /etc/opt/marzneshin/.env
```

### 2. Set Chat ID and Bot Token

Set the following values in the `.env` file. To get these values, use the following resources:

- **Telegram Bot Token**: To get a bot token, create a new bot via [@BotFather](https://t.me/botfather) on Telegram.

```bash
TELEGRAM_API_TOKEN = 123456789:XXXXXXXXXXXXXXXX
```

- **Admin Chat ID**: Use [@chatidbot](https://t.me/userinfobot) to get your chat ID.

```bash
TELEGRAM_ADMIN_ID = 123456789
```

- **Telegram Channel (Optional)**: Use [@chatidbot](https://t.me/userinfobot) to get the chat ID of your Telegram channel.

```bash
TELEGRAM_LOGGER_CHANNEL_ID = -1234567890123
```

- **Telegram Proxy URL (Optional)**: If you are using a proxy, enter your proxy URL here.

```bash
TELEGRAM_PROXY_URL = "http://localhost:8080"
```

### 3. Restart the Marzneshin Service

After setting the values, restart the Marzneshin service to apply the changes:

```bash
marzneshin restart
```

From now on, you will receive notifications related to users.

{{% /steps %}}
