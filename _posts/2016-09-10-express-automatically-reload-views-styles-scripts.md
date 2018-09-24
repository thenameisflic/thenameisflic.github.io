---
id: 155
title: "Express: How to automatically reload views, styles and scripts"
date: 2016-09-10T23:05:26+00:00
author: flic
layout: single
guid: http://www.thenameisflic.com/?p=155
permalink: /express-automatically-reload-views-styles-scripts/
categories:
  - express
tags:
  - express
  - livereload
  - node
  - webpack
---

Today we are going to take a look at an example i just built showing how you can automatically absolutely everything in an Express application. And with everything, i mean that once you change your styles, your client scripts or even your server data, your browser automatically refreshes with the new data. Yes, you heard it right: **whenever you change any single bit of your app, it automatically refreshes in every connected browser.** [Check the example now on Github](https://github.com/flicsl/express-example-hot-reload-everything).

# How do you do it?

In this example, i&#8217;ve used an absolutely magical combination: Express, Livereload and Webpack. I&#8217;m assuming you have a basic idea of what Express is (and if you don&#8217;t, check out their [Hello World guide](https://expressjs.com/en/starter/hello-world.html) right now!). [Livereload](https://www.npmjs.com/package/live-reload) is basically a server that watches for changes in files and sends messages to every connected client. We&#8217;re also putting [Webpack](https://webpack.github.io/) in the mix so that we have an easy way to bundle our project dependencies.

<div id="attachment_156" style="width: 373px" class="wp-caption aligncenter">
  <img class="wp-image-156 " src="http://104.236.4.255/wp-content/uploads/2016/09/10X7N1QVZL-300x200.jpg" alt="Express with Coke and M&M's" width="363" height="242" />
  
  <p class="wp-caption-text">
    A mix as awesome as M&Ms with Coke.
  </p>
</div>

# Grab the example and happy coding!

Its unfortunately somewhat tricky to get everything going, but i&#8217;ve done all the hard work so you don&#8217;t have to. Just [grab the code on Github](https://github.com/flicsl/express-example-hot-reload-everything) and enjoy a turbo speed development!
