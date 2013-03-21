---
title: 'Reading Phone Numbers, Access Codes with Twilio&#8217;s Speech Engine'
author: Matt
layout: post
permalink: /2010/12/reading-phone-numbers-access-codes-with-twilios-speech-engine/
categories:
  - Development
tags:
  - php
---
# 

Here’s a quick tip on how to get [Twilio][1] to read a phone number, access code, or how to spell out a word to users with the Twilio [speech engine][2]. The Python function below will take in any string, split the string into multiple characters, and then add a space and comma between each character. The result is that Twilio will say each letter or number separately at a slower speed.

 [1]: http://www.twilio.com
 [2]: http://www.twilio.com/docs/api/2010-04-01/twiml/say



Without separating the characters, Twilio’s speech engine understands “ABC123” as a word and attempts to read it. But when you send “A, B, C, 1, 2, 3,” in your TwiML, Twilio will read this naturally, at a speed slow enough that the caller can write it down. This is useful when reading phone numbers or access codes, depending on your service. This is a little tricky in Python, so I thought I’d share this.