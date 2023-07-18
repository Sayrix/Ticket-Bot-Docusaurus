---
sidebar_position: 6
---

# ⚠️ Common Errors

## You Didn't Follow Doc Error
If you see any of this errors, then it's likely you didn't follow the doc like you're suppose to and get any of the following errors.
*  `The table main.config does not exist in the current database` - You did not run the `npm run setup`
* `Cannot find module '.../dist/index.js'` - You did not run `npm run build`
* `Used disallowed intents` - You did not enable all the intent for the bot
* `Must be between 1 and 25 in length` - You have more than 25 `ticketType` in your config or have an invalid/out-of-date config which result in 0 `ticketType` available
    * For newer source, this should be replaced with appropriate message
* `An invalid token was provided` - either the token you provided was actually invalid or you didn't setup the environment variable correctly. It's most likely the latter that happens.
* `The provided value for the column is too long for the column's type. Column: *` - You did not use the schema on the doc site like ur suppose to to

To avoid any more errors, re-read the whole doc and confirm you have followed all of it before continuing.

## General Errors
This is a general errors that you might encounter
* `Websocket Error: 1001/1006` - This is some issues with Cloudflare WS connection, you can safely ignore it