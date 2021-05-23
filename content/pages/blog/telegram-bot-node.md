---
title: lorem-ipsum
subtitle: lorem-ipsum
date: '2021-05-22'
thumb_image_alt: lorem-ipsum
image_alt: A Bot
excerpt: lorem-ipsum
seo:
  title: ''
  description: ''
  robots: []
  extra: []
  type: stackbit_page_meta
layout: post
thumb_image: /images/alex-knight-2EJCSULRwC8-unsplash.jpg
image: /images/alex-knight-2EJCSULRwC8-unsplash.jpg
---
I enjoy looking for new technologies to experiment with during my free time, last weekend I stumbled across IBM Watson. It has numerous interesting services, so I thought it would be nice to use it in a project. In this article, I will guide you through the entire process of building a speech-to-text Telegram bot.

### Here is a table with our sections:

*   Set up your bot with the BotFather

*   Get your Watson API key

*   Set up environment

*   Set up the convert.js file

*   Create the bot.js file

*   Run your bot

## Set up your bot with the BotFather

Creating our Telegram bot is very simple, first, navigate to the [BotFather](https://t.me/botfather) and start a chat to get your API key.

After creating a new bot, the bot father will prompt you to enter a name and a username. After entering the credentials, you will be provided with your access token, save this token for later.

\*\*Keep your secrets safe
\*\*Please keep your keys safe, as anyone who has access to them can use them. For this reason, we will create a **.env** file to store them. Ensure to add the file to your **.gitignore** file.

###

## Get your IBM API Key

We will use its speech-to-text API. Head over to [ibm watson](https://www.ibm.com/watson) and create an account if you don't have one.

Once logged in, sign up for IBM cloud:

Create your IBM cloud account and sign in

Create a new speech-to-text resource.

Navigate to your speech-to-text dashboard and copy your API Key

Now we are ready to start coding our bot!

## &#xA;Environment set up:

Now that we have our access token and API key, we can begin coding our bot. Let’s start by heading to our terminal and creating a folder named telegram-bot. Use npm init -y to create your package.json file.

```
$ mkdir telegram-bot && cd telegram-bot
$ npm init -y

```

Then, head over to your terminal and create the following files.

    $ touch bot.js convert.js .env

Our bot.js file will contain the logic to handle requests to our bot. Our convert.js file will handle the function that will call on the IBM speech-to-text API. Finally, we will keep our secrets in the .env file.

Install dependencies

    $ npm install telegraf axios ibm-watson dotenv

*   Telegraf is a library that simplifies creating Telegram bots, read more its documentation [here](https://telegraf.js.org/).

*   Axios is a library that simplifies making HTTP requests

*   ibm-watson is SDK that allows us to interact with the Watson API, read more on the speech to text documention [here](https://cloud.ibm.com/docs/speech-to-text?topic=speech-to-text-gettingStarted#gettingStarted)

*   The dotenv package allows us to load our secrets

Add secrets to .env file:
You can name your secrets whatever you would like. Replace the brackets with your API keys.

    TELEGRAM_ACCESS_TOKEN=<Replace with token>
    IBM_API=<Replace with token>

## Our convert.js

I'll copy the code for the convert.js and explain each step below.

```
const SpeechToTextV1 = require('ibm-watson/speech-to-text/v1');
const { IamAuthenticator } = require('ibm-watson/auth');
require('dotenv').config();

const speechToText = new SpeechToTextV1({
  authenticator: new IamAuthenticator({ apikey: process.env.IBM_API }),
  serviceUrl: 'https://api.us-south.speech-to-text.watson.cloud.ibm.com'
});

//function for tranlating text with IBM APIfunction getText(audio) {
  const params = {
    audio: audio,
    contentType: 'audio/ogg'
  };
  return new Promise((resolve, reject) => {
    speechToText.recognize(params)
    .then(response => {
      const message = response.result.results;
      if(message.length === 0) {
          resolve('Please speak louder, unable to translate');
      }
      resolve(message[0].alternatives[0].transcript);
    })
    .catch(err => {
      reject(err);
    });
  })}

module.exports = getText;

```

```
const SpeechToTextV1 = require('ibm-watson/speech-to-text/v1');
const { IamAuthenticator } = require('ibm-watson/auth');
require('dotenv').config();

const speechToText = new SpeechToTextV1({
  authenticator: new IamAuthenticator({ apikey:process.env.IBM_API }),
  serviceUrl: 'https://api.us-south.speech-to-text.watson.cloud.ibm.com'
});

```

```

Here we import the 
```
