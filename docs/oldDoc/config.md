---
sidebar_position: 2
---

# ⚙️ Configuration

First you need to set the token of your bot in the `token.json`.  
Example:

```json
// config/token.json
{
  "token": "my.discord.bot.token"
}
```

To configure Ticket Bot, you need to edit the `config.jsonc` file in the `/config` folder.

```json
// config/config.jsonc
{
	"clientId": "1111111111111111111", // The id of the discord bot
	"guildId": "1111111111111111111", // The id of the discord server
	"mainColor": "f6c42f", // The hex color of the embeds by default
	"lang": "main", // If you want to set english please set "main"

	/*
	Pick a database driver, postgres will take priority over mysql (if both are enabled, which please don't do).
	If neither option is enabled, SQLite will be used.
		*PostgreSQL will be using default schema*
	*/
	"postgre": {
		"enabled": false,
		"host": "postgresql.example.com", // The host of the PostgreSQL database
		"user": "postgres", // The user of the PostgreSQL database
		"password": "password", // The password of the PostgreSQL database
		"database": "postgres", // The name of the PostgreSQL database
		"table": "json" // The name of the table where the tickets will be saved
	},
	"mysql": {
		"enabled": false,
		"host": "mysql.example.com", // The host of the MySQL database
		"user": "mysql", // The user of the MySQL database
		"password": "password", // The password of the MySQL database
		"database": "ticketbot", // The name of the MySQL database
		"table": "json" // The name of the table where the tickets will be saved
	},

	"closeTicketCategoryId": "", // The id of the category where a closed ticket will be moved to. Leave blank to disable this feature

	"openTicketChannelId": "1111111111111111111", // The id of the channel where the message to create a ticket will be sent

	"ticketTypes": [
		// You have a limit of 25 types (the limit of Discord)
		{
			"codeName": "category-one", // The name need to be in lowercase
			"name": "Category One", // The name that will be displayed in the ticket
			"description": "Description of Category One", // The description of the Ticket in Create Ticket Menu
			"emoji": "💡", // The emoji of the type (can be blank)
			"color": "", // Can be a hex color or blank to use the main color
			"categoryId": "1111111111111111111", // The category id where the tickets will be created
			"ticketNameOption": "💡ticket-TICKETCOUNT", // Here is all parameter: USERNAME, USERID, TICKETCOUNT (set to blank to use the default name)
			"customDescription": "", // The custom description of the ticket type, here is all parameter: USERNAME, USERID, TICKETCOUNT, REASON1, 2, ect (set to blank to use the default description)
			"cantAccess": ["1111111111111111111"], // The roles who can't access to this ticket type
			"askQuestions": false, // If the bot should ask the reason of the ticket
			"questions": [] // Leave blank if you don't want to ask questions
		},
		{
			"codeName": "category-two", // The name need to be in lowercase
			"name": "Category Two", // The name that will be displayed in the ticket
			"description": "Description of Category Two", // The description of the Ticket in Create Ticket Menu
			"emoji": "🛑", // The emoji of the type (can be blank)
			"color": "#f8312f", // Can be a hex color or blank to use the main color
			"categoryId": "1111111111111111111", // The category id where the tickets will be created
			"ticketNameOption": "", // Here is all parameter: USERNAME, USERID, TICKETCOUNT (set to blank to use the default name)
			"customDescription": "Please explain your report in detail. If you have any images, please attach them to your message.", // The custom description of the ticket type, here is all parameter: USERNAME, USERID, TICKETCOUNT, REASON1, 2, ect (set to blank to use the default description)
			"cantAccess": ["2222222222222222222"], // The roles who can't access to this ticket type
			"askQuestions": false, // If the bot should ask the reason of the ticket
			"questions": [] // Leave blank if you don't want to ask questions
		},
		{
			"codeName": "other", // The name need to be in lowercase
			"name": "Other", // The name that will be displayed in the ticket
			"description": "Description of Category Other", // The description of the Ticket in Create Ticket Menu
			"emoji": "", // The emoji of the type (can be blank)
			"color": "", // Can be a hex color or blank to use the main color
			"categoryId": "1111111111111111111", // The category id where the tickets will be created
			"ticketNameOption": "", // Here is all parameter: USERNAME, USERID, TICKETCOUNT (set to blank to use the default name)
			"customDescription": "Thank you for your ticket, a staff will reply you as soon as possible\n\n__**What is the reason of the ticket?**__: REASON1", // The custom description of the ticket type, here is all parameter: USERNAME, USERID, TICKETCOUNT, REASON1, 2, ect (set to blank to use the default description)
			"cantAccess": [], // The roles who can't access to this ticket type
			"askQuestions": true, // If the bot should ask the reason of the ticket
			"questions": [
				{
					"label": "What is the reason of the ticket?",
					"placeholder": "Please enter the reason",
					"style": "PARAGRAPH", // SHORT or PARAGRAPH
					"maxLength": 1000
				}
			]
		}
	],
	"ticketNameOption": "Ticket-TICKETCOUNT", // Here is all parameter: USERNAME, USERID, TICKETCOUNT
	"ticketNamePrefixWhenClaimed": "✔️", // With ✔️ as prefix the name of the ticket will be like this: ✔️ticket-1

	"rolesWhoHaveAccessToTheTickets": ["1111111111111111111", "2222222222222222222"], // Roles who can access to the tickets (Like the staff)

	"rolesWhoCanNotCreateTickets": [], // Roles who can	not create a tickets (Like a blacklist)

	"pingRoleWhenOpened": true,
	"roleToPingWhenOpenedId": ["1111111111111111111"], // The role to ping when a ticket is opened

	"logs": true,
	"logsChannelId": "1111111111111111111", // The id of the channel where the logs will be sent

	"claimButton": true,

	"whoCanCloseTicket": "STAFFONLY", // STAFFONLY (roles configured at "rolesWhoHaveAccessToTheTickets") or EVERYONE
	"closeButton": true, // If false the ticket can be closed only by doing /closes
	"askReasonWhenClosing": true, // If false the ticket will be closed without asking the reason

	"createTranscript": true, // If set to true, when the ticket is closed a transcript will be generated and sent in the logs channel

	"status": {
		"enabled": true, // If you want to enable the status of the bot
		"text": "github.com/Sayrix", // The text of the status
		"type": "PLAYING", // PLAYING, WATCHING, LISTENING, STREAMING, COMPETING
		"url": "https://twitch.tv/grimkujow", // The url of the status if the type is STREAMING (can be blank)
		"status": "online" // online, idle, dnd, invisible set to online if the type is STREAMING
	},

	"maxTicketOpened": 0 // The number of tickets the user can open while another one is already open. Set to 0 to unlimited
}
```

## Change some embeds

If you want to change some embeds, you can edit the json of locales in the `/locales` folder. By default the bot use `main.json` but you can edit it to use another language.
