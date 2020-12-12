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
<img title="a title" alt="Alt text" src="https://assets.digitalocean.com/articles/node_discord_bot/step1a.png">

To get started, click New Application. Discord will ask you to enter a name for your new application. Then click Create to create the application.
<img title="a title" alt="Alt text" src="https://assets.digitalocean.com/articles/node_discord_bot/step1b.png">


Now open up your application dashboard. To add a bot to the application, navigate to the Bot tab on the navigation bar to the left.
<img title="a title" alt="Alt text" src="https://assets.digitalocean.com/articles/node_discord_bot/step1c.png">


Click the Add Bot button to add a bot to the application. Click the Yes, do it! button when it prompts you for confirmation. You will then be on a dashboard containing details of your bot’s name, authentication token, and profile picture. Dont forget to copy the token and paste it in the code where it says TOKEN HERE You can find a image of the code here! 
<img title="a title" alt="Alt text" src="https://media.discordapp.net/attachments/786342174638997514/786698810482491392/unknown.png">

<img title="a title" alt="Alt text" src="https://assets.digitalocean.com/articles/node_discord_bot/step1d.png">

You can modify your bot’s name or profile picture here on the dashboard. You also need to copy the bot’s authentication token by clicking Click to Reveal Token and copying the token that appears.

Warning: Never share or upload your bot token as it allows anyone to log in to your bot.

Now you need to create an invite that allows you to add the bot Discord guilds where you can test the bot. First, navigate to the OAuth2 tab of the application dashboard. To create an invite, scroll down and select bot under scopes. You must also set permissions to control what actions your bot can perform in guilds. For the purposes of this tutorial, select Administrator, which will give your bot permission to perform nearly all actions in guilds. Copy the link with the Copy button.
<img title="a title" alt="Alt text" src="https://assets.digitalocean.com/articles/node_discord_bot/step1e.png">


Then invite the bot
<img title="a title" alt="Alt text" src="https://media.discordapp.net/attachments/786342174638997514/786694221968441354/unknown.png">


Click continue 
<img title="a title" alt="Alt text" src="https://media.discordapp.net/attachments/786342174638997514/786694286455996457/unknown.png">



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


### Command Handler

Create a file called index.js

Inside put:

```javascript

const Discord = require("discord.js"),
      client = new Discord.Client(),
      fs = require("fs");
//Command Handler
client.commands = new Discord.Collection();
client.aliases = new Discord.Collection();
client.events = new Discord.Collection();

fs.readdir("./commands/", (err, files) => {
    if (err) return console.log(err);
    files.forEach(file => {
        if (!file.endsWith(".js")) return;
        let props = require(`./commands/${file}`);
        console.log("Successfully loaded " + file)
        let commandName = file.split(".")[0];
        client.commands.set(commandName, props);
    });
});
    //Events "handler"
    fs.readdir('./events/', (err, files) => {
        if (err) console.log(err);
        files.forEach(file => {
            let eventFunc = require(`./events/${file}`);
            console.log("Successfully loaded " + file)
            let eventName = file.split(".")[0];
            client.on(eventName, (...args) => eventFunc.run(client, ...args));
        });
});

client.on("ready", () => console.log("Online!"));
client.login('Token Here!')
```

Message Event

Create a file called message.js in a folder called events.
Now we will use our message event code!

```javascript
const prefix = "Your desired prefix here!"  

 exports.run = async(client, message) => {
  if (message.author.bot) return;
  if (message.content.startsWith(prefix)) {
    
 let messageArray = message.content.split(" "),
     cmd = messageArray[0],
     args = messageArray.slice(1),
     commandfile = client.commands.get(cmd.slice(prefix.length)) || client.aliases.get(cmd.slice(prefix.length));
  
if(!commandfile) return;    
    commandfile.run(client,message,args);             
  }
  


```

Example command

```javascript
exports.run = (client, message, args) => {
  message.channel.send("Pong :)");
}
exports.config = {
  aliases: ["pong", "pingpong"]
}

```
