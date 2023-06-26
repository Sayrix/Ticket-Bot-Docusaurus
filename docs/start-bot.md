---
sidebar_position: 3
---

# 🚀 Start the bot

Before starting the bot, make sure you transpile the ts source first by running `npm run build`.

Now to start it, you need to run the command `npm start` (or `node dist/index.js`) in the terminal.	
You can also use a process manager like [PM2](https://pm2.keymetrics.io/).

## Update the bot
If you're using `git clone` as way to obtain the source, the easiest way to update is by running the following commands:
```bash
git pull
npm run build
```
If there's any issues due to a change in Prisma models. Run the setup command again via `npm run setup`

## Keep the bot online 24/7

To keep the bot online 24/7 I can host your bot for $1/month. For more information, you can contact me on Discord (`@sayrix`)
Or host the bot on a Server/VPS.