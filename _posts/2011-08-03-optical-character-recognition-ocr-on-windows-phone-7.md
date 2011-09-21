--- 
layout: post
title: Optical Character Recognition on Windows Phone 7
published: true
meta: 
  aktt_notify_twitter: "yes"
  _edit_last: "1"
  _efficient_related_posts: "a:6:{i:0;a:4:{s:2:\"ID\";s:3:\"145\";s:10:\"post_title\";s:50:\"Early Look at Mojito: Mint.com for Windows Phone 7\";s:7:\"matches\";s:1:\"6\";s:9:\"permalink\";s:81:\"http://mbmccormick.com/2011/08/early-look-at-mojito-mint-com-for-windows-phone-7/\";}i:1;a:4:{s:2:\"ID\";s:3:\"135\";s:10:\"post_title\";s:43:\"Application Development for Windows Phone 7\";s:7:\"matches\";s:1:\"5\";s:9:\"permalink\";s:75:\"http://mbmccormick.com/2011/07/application-development-for-windows-phone-7/\";}i:2;a:4:{s:2:\"ID\";s:2:\"83\";s:10:\"post_title\";s:51:\"Deploying an Application to AppHarbor in 10 Minutes\";s:7:\"matches\";s:1:\"4\";s:9:\"permalink\";s:83:\"http://mbmccormick.com/2011/03/deploying-an-application-to-appharbor-in-10-minutes/\";}i:3;a:4:{s:2:\"ID\";s:3:\"161\";s:10:\"post_title\";s:42:\"Bulk INSERT to SQL Azure using LINQ to SQL\";s:7:\"matches\";s:1:\"3\";s:9:\"permalink\";s:74:\"http://mbmccormick.com/2011/09/bulk-insert-to-sql-azure-using-linq-to-sql/\";}i:4;a:4:{s:2:\"ID\";s:2:\"98\";s:10:\"post_title\";s:27:\"Getting Ready for Microsoft\";s:7:\"matches\";s:1:\"3\";s:9:\"permalink\";s:59:\"http://mbmccormick.com/2011/05/getting-ready-for-microsoft/\";}i:5;a:4:{s:2:\"ID\";s:2:\"87\";s:10:\"post_title\";s:55:\"How I Launched 4sqtransit in Two Weeks on Windows Azure\";s:7:\"matches\";s:1:\"3\";s:9:\"permalink\";s:87:\"http://mbmccormick.com/2011/04/how-i-launched-4sqtransit-in-two-weeks-on-windows-azure/\";}}"
  aktt_tweeted: "1"
  _relation_threshold: "3"
tags: 
- api
- c#
- cloud
- internet
- microsoft
- Projects
- silverlight
- summer
- wp7
type: post
status: publish
---
I'm working on a new <a href="http://www.microsoft.com/windowsphone/en-us/default.aspx" target="_blank">Windows Phone</a> application that uses some new <a href="http://www.engadget.com/2011/05/24/microsoft-announces-windows-phone-mango-update-early-and-in/" target="_blank">Mango features</a>, which has been a pretty fun project thus far. Mango has some new functionality that I need access to, namely the <a href="http://www.windowsphonegeek.com/tips/8-How-to-use-SaveContactTask-in-Windows-Phone-Mango" target="_blank">ability to save contacts</a> to the phone's address book. However, this post is going to talk about some additional functionality available for Windows Phone 7 that is enabled through <a href="http://research.microsoft.com/en-us/um/redmond/projects/hawaii/" target="_blank">Project Hawaii</a>, developed by <a href="http://research.microsoft.com/en-us/" target="_blank">Microsoft Research</a>.

The Hawaii Cloud Services SDK for WP7 has several cloud-based services including a <a href="http://research.microsoft.com/en-us/um/redmond/projects/hawaii/download/HowToUseTheHawaiiRelayService.pdf" target="_blank">Relay Service</a>, Rendezvous Service, <a href="http://research.microsoft.com/en-us/um/redmond/projects/hawaii/download/HowToUseTheSpeechToTextService.pdf" target="_blank">Speech to Text</a>, and <a href="http://research.microsoft.com/en-us/um/redmond/projects/hawaii/download/HowToUseTheHawaiiRelayService.pdf" target="_blank">Optical Character Reading (OCR) Service</a>. You can read up on what each of these can do, but for now I will focus on the OCR service. My new Windows Phone 7 application is called Carded and will allow you to take a picture of a business card and import the contact information from that card into your phone's contacts list. To do that, I am using the OCR service from Project Hawaii to read an image and return the text in that image.

To get access to Project Hawaii, you first need to download and install the Hawaii Cloud Services SDK for WP7 for use in your project. Next, you need to generate an API key at the <a href="http://hawaiiguidgen.cloudapp.net/" target="_blank">Project Hawaii Signup</a> page. Here, you will login with your Live ID and the website will generate a GUID for you to use in your application.

[gist id=1121868]

Now to actually take a picture on Windows Phone 7, you need to use the <code>CameraCaptureTask</code> as shown below.

[gist id=1121897]

Once the application has the picture, it's time to call the OCR service. Here's where the Hawaii SDK comes into play, in the code below we convert the image into a byte stream and submit this to the Hawaii Service.

[gist id=1121901]

Once the Hawaii OCR service returns with our results, we can then parse this text data.

[gist id=1121905]

And with that, we can begin to further parse this text data into relevant information. This is where the fun part of my application exists: trying to parse phone nubmers, email address, job titles, names, company names, etc. and distinguish this in a way that makes sense to the user in the form of a contact entry. I'm sure another blog post will ensue once I figure out how to accomplish this.
