# Cookie-Dash-Button
A program that sends an SMS message and a Tweet when fresh cookies are delivered at my favorite coffee shop.


# Send an SMS message with your Dash Butotn
Follow these <a href="https://github.com/sanzgiri/dash-sms">Dash SMS</a> to find your Dash Button's MAC address and set up the function to send an SMS message. You'll also need to set up a Twilio account for this.


# Post a Tweet with your Dash Button
I found most of my information for this part of the project on this <a href="https://node-twitter.com/">Twitter for Node.js</a> page.

You'll need to set up a Twitter Developer account to create an app and receive your Consumer Keys and Access Tokens.

```
const Twitter = require('twitter');

const clienttwitter = new Twitter({
  consumer_key: ' ', // these keys are all found in your Twitter Developer account settings
  consumer_secret: ' ', 
  access_token_key: ' ',
  access_token_secret: ' '
});

const params = {screen_name: 'twitter_username'};
```

Here's what my function looks like to post a Tweet when the Dash Button is pressed:

```
console.log('waiting for dash button to be pressed...');
dash.on('detected', () => {
  console.log('Dash button detected!');

function postTweet() {
      clienttwitter.post('statuses/update', {status: 'The cookies have been delivered!'}, function(error, tweet, response) {
      if(error) throw error;
      console.log(tweet);
      console.log(response);
      
setTimeout(postTweet, tweetDelay);
```

I also wanted to add in a delay, so that the Tweet is posted 20 minutes after the text is sent. I did this to give myself a headstart, so I could grab a fresh cookie before anyone else. To do that, I used a setTimeout function.

I added this tweetDelay of 1,200,000 milliseconds up underneath my Twitter credentials.

```
var tweetDelay = 1200000; // how long of a delay you want, in milliseconds
```

# Acknowledgements
Ashutosh Sanzgiri (https://github.com/sanzgiri/dash-sms) - I grabbed a lot of this code to get started.
