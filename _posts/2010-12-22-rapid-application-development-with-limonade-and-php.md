﻿---
layout: post
title: Rapid Application Development with Limonade and PHP
author: Matt
permalink: /2010/12/rapid-application-development-with-limonade-and-php/
categories:
  - Development
tags:
  - php
---

Recently, I've been working on the first product for McCormick Technologies (more information about that to come). My application started out as a very simple utility that I was using for internal workflows and over the past couple of months the feature set has really grown. I decided that it was time to move to a MVC framework to keep the application organized and reduce duplicate code. So I began searching for a light-weight MVC framework for PHP, or "micro-framework" as it's called.

I read through several different forum threads and blog posts, and most people talked about a framework called [Sinatra][1] for Ruby. I decided to look at what Sinatra had to offer to get a better idea of what I was looking for. The nice thing about Sinatra is that it essentially is a URL-rewriting framework with views and controllers, without the models. At first I was concerned about not having this feature, but after looking at the code examples that Sinatra had on it's website, I was reassured.

 [1]: http://www.sinatrarb.com/

So I did some more research and found three of these Sinatra-style frameworks for PHP. The first was [Nicedog][2] a "nano web framework for PHP, like web.py for Python, Sinatra or Camping for Ruby". After playing around with Nicedog, I found it extremely difficult to get up and running. There was just too much going on behind the scenes for comfort. The next framework I looked at was actually a fork of Nicedog, called [Tyke][3]. Tyke simplified some of the work needed to implement Nicedog and had more documentation on the framework, but it was still not what I was looking for.

 [2]: https://github.com/bastos/nicedog
 [3]: https://github.com/digitarald/tyke

After more research, I settled with [Limonade][4], a "PHP micro framework for rapid web development and prototyping". What set Limonade apart from the rest of the frameworks that I looked at is that the documentation available for the framework was extremely thorough. There were several example websites that were built using Limonade and additional documentation of each and every feature of the framework. Here's how easy it is to get started with Limonade:

 [4]: http://www.limonade-php.net/

<script src="https://gist.github.com/mbmccormick/752574.js"> </script>

This framework even has support for controllers, which was something I wanted without having to implement it myself. It also has support for views, which allows for clean separation of application logic and HTML code. It also has support for additional features like error handling, custom `.htaccess` files, and advanced session capabilities.

All in all, Limonade is a great framework that is easy to learn and has the capabilities of heavier frameworks, without the bloat. More information about my upcoming product, and how Limonade is used in it, will be coming soon after the new year.
