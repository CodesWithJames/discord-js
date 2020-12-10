## Build a discord.js bot!



### Installation!

You will need node.js hich is installed at http://nodejs.org/ follow the steps on the installation guide. Open command prompt (cmd). Make a folder in desktop.

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


### More advanced commands!

COMING SOON!

