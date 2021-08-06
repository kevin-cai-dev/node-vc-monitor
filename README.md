# node-vc-monitor

[DEV Bot link](https://discord.com/api/oauth2/authorize?client_id=872840310097584159&permissions=3088&scope=bot) \

This project aims to provide a Discord bot which alerts subscribed users
whenever new activity is detected in the specified voice channels.\
Made using Node.js, DiscordAPI, MongoDB.

You can access the bot [here](https://discord.com/api/oauth2/authorize?client_id=859728389883953163&permissions=142480&scope=bot).

Credit to the [Discord.js Guide](https://discordjs.guide/ "Discord.js Guide
Homepage") and [Discord.js documentation](https://discord.js.org/#/docs/main/stable/general/welcome
"Discord.js documentation") for providing guides to aid in the development of
the bot.

WARNING: This bot has not been fully tested and may contain bugs. If you ever
want to use it, be careful. Performance across multiple servers has not been
tested very thoroughly (since I don't have many servers to test it on) and may
produce unexpected results. It utilises privileged intents and so its capability
is limited to < 100 servers before needing to be verified/whitelisted.

### Design Explanation
Originally designed in python using the discord.py library, I opted to redevelop the bot using Node.js and Discord.js to hopefully incorporate both front-end and back-end features.

Currently, I use a MongoDB database to store servers, voice channels and user subscriptions. It is currently hosted by me on Heroku. This is a self-project aimed to both provide a useful service as well as
allowing me to learn new tools.

### TODO
server has an array of user references CHECK

when adding server, create new vc documents, create new user documents if not in
database, else increment user servercount by 1

when deleting server, remove vc documents and decrement servercount for all
users by 1. if servercount == 0, remove user document

when updating server, consider user join/leave logic

when user leaves, remove reference from server and decrement servercount by 1.
if servercount == 0, remove user document

when user joins, add reference to server and if user already exists increment
servercount by 1. else create new user document and add reference

when vc is created, go through all users in server and check for autosub flag.
if true, add to vc list

modify any checks for vc users to populate and map userID first before operating