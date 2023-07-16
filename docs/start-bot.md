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
If there is any changes to the Prisma models or the database type, run the setup command again via `npm run setup`.

If you're using external database, you may encounter issues when trying to run `git pull`. To fix it:
1. run `git reset --hard HEAD`
2. Continue with the regular update process
3. Follow the [Prisma Setup](https://doc.ticket.pm/docs/prisma) to set the schema back

## Keep the bot online 24/7

To keep the bot online 24/7, you can sponsor [Sayrix on github](https://github.com/sponsors/Sayrix) and benefit from other advantages and, depending on your tier, get multiple hostings for cheap.
Or host the bot on a Server/VPS.
