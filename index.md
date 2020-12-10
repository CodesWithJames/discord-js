## Build a discord.js bot!



### Installation!

You will need node.js which is installed at http://nodejs.org/ follow the steps on the installation guide. Open command prompt (cmd). Make a folder in desktop.

On cmd type:

```markdown
cd desktop
then
cd folder name
then
npm install discord.js
```


### Coding your bot.

Open your code editor, mine is Visual Studio Code.
Open the folder for your bot in the editor, make a file and name it index.js.
Then open command prompt (cmd).

```javascript
const Discord = require('discord.js');
const client = new Discord.Client();

client.on('ready', () => {
  console.log(`Logged on as ${client.user.tag}!`);
});

client.on('message', msg => {
  if (msg.content === '!ping') {
    msg.reply('Pong!');
  }
});

client.login('TOKEN HERE');
```


### Grab your token

Set up a Discord bot and get the bot’s token, which you will pass into your program.

In order to register a bot on the Discord platform, use the Discord application dashboard https://discord.com/developers/applications/. Here developers can create Discord applications including Discord bots.
[image1]: https://assets.digitalocean.com/articles/node_discord_bot/step1a.png "Logo Title Text 2"

To get started, click New Application. Discord will ask you to enter a name for your new application. Then click Create to create the application.
[image1]: https://assets.digitalocean.com/articles/node_discord_bot/step1b.png "Logo Title Text 2"


Now open up your application dashboard. To add a bot to the application, navigate to the Bot tab on the navigation bar to the left.
[image1]: https://assets.digitalocean.com/articles/node_discord_bot/step1c.png "Logo Title Text 2"


Click the Add Bot button to add a bot to the application. Click the Yes, do it! button when it prompts you for confirmation. You will then be on a dashboard containing details of your bot’s name, authentication token, and profile picture.
[image1]: https://assets.digitalocean.com/articles/node_discord_bot/step1d.png "Logo Title Text 2"

You can modify your bot’s name or profile picture here on the dashboard. You also need to copy the bot’s authentication token by clicking Click to Reveal Token and copying the token that appears.

Warning: Never share or upload your bot token as it allows anyone to log in to your bot.

Now you need to create an invite that allows you to add the bot Discord guilds where you can test the bot. First, navigate to the OAuth2 tab of the application dashboard. To create an invite, scroll down and select bot under scopes. You must also set permissions to control what actions your bot can perform in guilds. For the purposes of this tutorial, select Administrator, which will give your bot permission to perform nearly all actions in guilds. Copy the link with the Copy button.
[image1]: https://assets.digitalocean.com/articles/node_discord_bot/step1e.png "Logo Title Text 2"

Then invite the bot
[image1]: https://media.discordapp.net/attachments/786342174638997514/786694221968441354/unknown.png "Logo Title Text 2"


Click continue 
[image1]: https://media.discordapp.net/attachments/786342174638997514/786694286455996457/unknown.png "Logo Title Text 2"



### Host

On cmd run 

```markdown
node index.js
```


### New commands

```javascript
client.on('message', msg => {
  if (msg.content === '!newcommand') {
    msg.reply('Newcommand!!!!');
  }
});

```
