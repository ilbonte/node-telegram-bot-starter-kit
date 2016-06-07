# node-telegram-bot-starter-kit
How to set up a Telegram Bot using Node.js and [node-telegram-bot-api](https://github.com/yagop/node-telegram-bot-api)
# Instructions

## Choose your hosting
1. I will use www.openshift.com because it offers a free plan.

2. Sign in and click on “Add Application” or “Create your first application now” 

3. Select NodeJs 0.10 cartridge 
![alt text](https://raw.githubusercontent.com/ilbonte/node-telegram-bot-starter-kit/master/1.png)

4. Choose your public url and the region then click “Create Application” (this may take a few seconds)

5. In the next step click “Yes, help me get started” and insert your public SSH key.
If you already have a key it can be found in “c:\Users\YOUR_USERNAME\\.ssh\id_rsa.pub” if you are on windows, otherwise in “~/.ssh/id_rsa”
![alt text](https://raw.githubusercontent.com/ilbonte/node-telegram-bot-starter-kit/master/2.png)

6. Press “Save” 

## Set up your repo and install -S node-telegram-bot-api

1. Clone the repository using the provided url
![alt text](https://raw.githubusercontent.com/ilbonte/node-telegram-bot-starter-kit/master/3.png)

2. Enter the nodejs folder

3. Run from the terminal `npm install node-telegram-bot-api`
![alt text](https://raw.githubusercontent.com/ilbonte/node-telegram-bot-starter-kit/master/4.png)

4. Open the file `server.js` and substitute the code with the example provided by https://github.com/yagop/node-telegram-bot-api

```js
var TelegramBot = require('node-telegram-bot-api');

var token = 'YOUR_TELEGRAM_BOT_TOKEN';
// Setup polling way
var bot = new TelegramBot(token, {polling: true});

// Matches /echo [whatever]
bot.onText(/\/echo (.+)/, function (msg, match) {
  var fromId = msg.from.id;
  var resp = match[1];
  bot.sendMessage(fromId, resp);
});

// Any kind of message
bot.on('message', function (msg) {
  var chatId = msg.chat.id;
  // photo can be: a file path, a stream or a Telegram file_id
  var photo = 'cats.png';
  bot.sendPhoto(chatId, photo, {caption: 'Lovely kittens'});
});
```

## Get your token

5. Open Telegram and search for BotFather (https://telegram.me/botfather)
  * Write `/newbot`
  * Write the name of your bot
  * Write the username of your bot
  * Copy your token and substitute it to “YOUR_TELEGRAM_BOT_TOKEN” in the file server.js
  ![alt text](https://raw.githubusercontent.com/ilbonte/node-telegram-bot-starter-kit/master/6.png)

## Deploy 

1. `git add --all`
2. `git commit -am ”initial commit”`
3. `git push origin master`
This may take few seconds

Note: ignore failure messages. These errors are reported because our app is not listening to any port, but we don’t need to.

## Enjoy 

Open your bot on Telegram and write /echo “write-something” and it should reply with the same message you wrote

![alt text](https://raw.githubusercontent.com/ilbonte/node-telegram-bot-starter-kit/master/7.png)

Inspired by: https://github.com/yukuku/telebot
