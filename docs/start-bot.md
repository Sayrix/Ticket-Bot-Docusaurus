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
If there is any changes to the Prisma models, run the setup command again via `npm run setup`.

If you're using external database, you may encounter issues when trying to run `git pull`. To fix it:
```md
1. Run `git reset --hard HEAD`
2. Run `git pull`
3. Go back to `prisma/schema.prisma` and change the `provider`
4. Run the `npm run setup` command **only if** there's a change to the original prisma model.
5. Run `npm run build`
```

## Keep the bot online 24/7

To keep the bot online 24/7 I can host your bot for $1/month. For more information, you can contact me on Discord (`@sayrix`)
Or host the bot on a Server/VPS.