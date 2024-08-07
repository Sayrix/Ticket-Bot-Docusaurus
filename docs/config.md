---
sidebar_position: 2
---

# ⚙️ Configuration

## Environment Variable
First, you should setup the environment variable by moving `.env.example` to `.env`

The configuration should contain
```bash
# Your discord token
TOKEN=""
# Prisma Database URL (refer to docs for more details)
DATABASE_URL="file:./tixbot.db"
```

Options:
* `TOKEN` - Your discord token goes here
* `DATABASE_URL` - The database conenction url (visit [Prisma Setup](https://doc.ticket.pm/docs/prisma) if you want to use different database)

Note for inexperienced users: .env is the default way of setting up the environment. If you're using services like replit, they'll provide you with a more secure way of storing environment variable, and you should use that instead.

## General Configuration
Next, setup the configuration file by moving `config/config.example.jsonc` to `config/config.jsonc` (`.jsonc` not `.json`)

Notes for `ticketTypes`:
* `codeName` cannot be duplicated.
* You technically can have more than 25 `ticketTypes`, but cannot show more than 25 at a time to user.
	* Easiest way to achieve that is by using `cantAccess`.

The configuration should contain
```jsonc title="/config/config.jsonc"
{
	"clientId": "1111111111111111111", // The id of the discord bot
	"guildId": "1111111111111111111", // The id of the discord server
	"mainColor": "#f6c42f", // The hex color of the embeds by default
	"lang": "main", // If you want to set english please set "main"

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
			"questions": [], // Leave blank if you don't want to ask questions
			"staffRoles": [] // Category specific staff role (instead of the default ones)
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
			"questions": [], // Leave blank if you don't want to ask questions
			"staffRoles": [] // Category specific staff role (instead of the default ones)
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
			"staffRoles": [], // Category specific staff role (instead of the default ones)
			"questions": [
				// Maximum of 5 questions can be set due to discord's limit
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

	// Ticket Claim Options
	"claimOption": {
		"claimButton": true, // Whether to enable ticket claim button or not
		// The X can be replaced with S (The staff that claimed the ticket) or U (The user that created the ticket)
		"nameWhenClaimed": "✔️ Ticket-TICKETCOUNT", // Here is all parameter: X_USERNAME, X_USERID, TICKETCOUNT
		"categoryWhenClaimed": "" // The category the ticket is moved to when claimed
	},

	"rolesWhoHaveAccessToTheTickets": ["1111111111111111111", "2222222222222222222"], // Roles who can access to the tickets (Like the staff)/ Treat this as global admin role type of thing.

	"rolesWhoCanNotCreateTickets": [], // Roles who can	not create a tickets (Like a blacklist)

	"pingRoleWhenOpened": true,
	"roleToPingWhenOpenedId": ["1111111111111111111"], // The role to ping when a ticket is opened

	"logs": true,
	"logsChannelId": "1111111111111111111", // The id of the channel where the logs will be sent
	
	"closeOption": {
		"closeButton": true, // If false the ticket can be closed only by doing /closes
		"dmUser": true, // Whether to DM the user when the ticket is closed
		"createTranscript": true, // If set to true, when the ticket is closed a transcript will be generated and sent in the logs channel
		"askReason": true, // If false the ticket will be closed without asking the reason
		"whoCanCloseTicket": "STAFFONLY", // STAFFONLY (roles configured at "rolesWhoHaveAccessToTheTickets") or EVERYONE
		"deleteTicket": false, // when enabled, it will delete the ticket on clicking close button
		"closeTicketCategoryId": "" // The id of the category where a closed ticket will be moved to. Leave blank to disable this feature
	},
	"uuidType": "uuid", // uuid or emoji

	"status": {
		"enabled": true, // If you want to enable the status of the bot
		"text": "github.com/Sayrix", // The text of the status
		"type": "PLAYING", // PLAYING, WATCHING, LISTENING, STREAMING, COMPETING
		"url": "https://twitch.tv/grimkujow", // The url of the status if the type is STREAMING (can be blank)
		"status": "online" // online, idle, dnd, invisible set to online if the type is STREAMING
	},

	"maxTicketOpened": 0, // The number of tickets the user can open while another one is already open. Set to 0 to unlimited
	/*
	Whether or not to minimizing the tracking data that are being sent
	Enabling this will cause the telemetry to only send the software version and node version
	*/
	"minimalTracking": false,
	// Hide internal websocket logs
	"showWSLog": false
}
```

## Change some embeds

If you want to change some embeds, you can edit the json of locales in the `/locales` folder. By default the bot use `main.json` but you can edit it to use another language.
