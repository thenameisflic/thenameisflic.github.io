---
id: 260
title: What everybody ought to know about building HTML5 web MMOs in 2017
date: 2017-01-29T22:06:08+00:00
author: flic
layout: single
guid: https://thenameisflic.com/?p=260
permalink: /what-everybody-ought-to-know-about-building-html5-web-mmos-in-2017/
image: /wp-content/uploads/2017/01/print-article2.png
categories:
  - MMOs
---

Hello, everybody! As you might know, recently i launched [Splash Wars](https://splashwars.io), an online shooter game. If you are willing to build your very own web MMO too, or just generally curious, here are some things you should know:

# Architecture is a pain

This topic is by far the one that hit me the hardest (and will probably hit you, too). Especially if you are going to use Node.JS, you simply won&#8217;t find any existing application architecture that you can simply drop in your project, and you&#8217;ll have to roll out your own. Be really careful with the decisions you take here, since architectural changes are the most complicated to make down the line! Here are some features your architecture will have to support:

- Game simulation: Move the players, collide bullets, etc.
- Network events: You need to notify every client when receiving user input, when user dies, etc.
- Timeline prediction: You don&#8217;t want to notify the clients every single event, so you&#8217;ll have to simulate those events at the browser.
- Renderers: How you&#8217;ll draw your game state? Remember to be aware of animations.
- Input validation on the server and on the client: Protect yourself from hackers! Don&#8217;t let the server accept everything.
- Many more, depending on the kind of game you want to make.

&nbsp;

# Optimizations for performance

That&#8217;s other topic that wasted many hours of mine during Splash Wars development: optimizing the clients. Even though our desktop machines are already powerful enough to not have trouble (well, most of the time) during rendering/updating the game, if you want to make your game compatible with mobile devices, you&#8217;ll have to put a lot of work into optimizing your render/update code.

The most important rule here is the same as any other application: make sure that you are measuring your performance. Google Chrome DevTools is great for that, so make sure to always run the Profiler before trying any optimizations. The 80-20 rule applies here: most of your benefits are going to come from simple changes on the code.

<div id="attachment_265" style="width: 1376px" class="wp-caption alignnone">
  <img class="size-full wp-image-265" src="https://thenameisflic.com/wp-content/uploads/2017/01/print-article2.png" alt="You have no idea of how much i love Dev Tools." width="1366" height="768" />
  
  <p class="wp-caption-text">
    You have no idea of how much i love Dev Tools.
  </p>
</div>

# Optimizing bandwidth and latency

Unless your game doesn&#8217;t involve too much realtime interaction, its unlikely plain text messages will work well. At the very least, you should send all your data in its binary format, what introduces lots of complexities by itself: for example, you&#8217;ll have to think about how many bits you might need and how to properly encode and decode messages.

Besides bandwidth, you&#8217;ll also have to worry about latency, otherwise your game might become unplayable. The core ideas to optimize the latency are simply making sure that your application responds quickly enough and that your servers are close to your players. The second part is a lot more expensive, but it can pay off big wins: by setting up a server in my country, i managed to cut the ping in half!

<div id="attachment_266" style="width: 1376px" class="wp-caption alignnone">
  <img class="wp-image-266 size-full" src="https://thenameisflic.com/wp-content/uploads/2017/01/print-article-1.png" width="1366" height="768" />
  
  <p class="wp-caption-text">
    Don&#8217;t even try to use Text messages!
  </p>
</div>

# Don&#8217;t forget physics

Depending on the architecture you chose for step 1, this might become easier for you. You should pay a great deal of attention to physics, since even slightly off hitboxes will have a huge impact in your players perception of the game.

I&#8217;ve had lots of trouble with it, but i managed to come up with a custom solution for rendering hitboxes that made physics a tad more manageable. This topic also ties with optimization, since the naive collision detection might work fine for most basic use cases and small amounts of elements, but will surely make your server/client hang as the amount of players increase.

# Wrapping up

I&#8217;ve mentioned a few factors that will surely come into play no matter what kind of MMO you are intending to make, but fortunately many of these problems have been solved before and turned into packages for your favorite programming language. If you are using NodeJS, you are lucky: npm is the biggest package repository out here, and most of the boilerplate code you can find there.

Nevertheless, building a MMO web game is still a formidable task, but definitely achievable and a very cool project to show to your friends, family and coworkers. If you have some free time to spare, give it a try and send me a link on Twitter (<http://twitter.com/thenameisflic>), i&#8217;ll be glad to play with you!
