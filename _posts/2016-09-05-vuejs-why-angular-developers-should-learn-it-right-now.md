---
id: 149
title: "VueJS: why AngularJS 1.x developers should learn it right now"
date: 2016-09-05T02:27:46+00:00
author: flic
layout: single
guid: http://www.thenameisflic.com/?p=149
permalink: /vuejs-why-angular-developers-should-learn-it-right-now/
categories:
  - angular
  - vue
---

In this post, i&#8217;m going to quickly summarise my initial impressions with the awesome new JS library [VueJS](https://vuejs.org/) . As a seasoned Angular 1.x developer, i am extremely excited for all the possibilities that this new library opens to us, as well as a much, **much** better organization to our web apps.

<div id="attachment_150" style="width: 819px" class="wp-caption aligncenter">
  <img class="wp-image-150" src="http://104.236.4.255/wp-content/uploads/2016/09/Captura-de-tela-de-2016-09-04-224813-300x112.png" alt="wego-vuejs-application" width="809" height="303" />
  
  <p class="wp-caption-text">
    A sample Vue.js application i built very easily with Feathers + Vue.
  </p>
</div>

# What exactly is Vuejs?

In their own words, Vuejs is a **view** library for MVVM development. This means that you&#8217;ll have to bring your own supporting libraries, since you are not going to have anything like Angular&#8217;s $http or $filter services. While that might look like a disadvantage at first, i found that it actually gave me way more freedom to mix and match as well as requiring only what i&#8217;m going to use, saving users a lot of network requests. Besides that, Vue.js is extremely lightweight, standing at an amazing 24kb when minified. Compare that against the 160kb your Angular.min.js required, and you can already see some benefits.

# Why should i spend my time learning it?

After spent a good deal of time getting the hang of it, thats honestly an easy question for me to answer:

1. Vue.js has an extremely **straightforward components API**. Instead of wasting your time debugging your Angular directives because the bindings aren&#8217;t working for some reason, you can simply declare which values your components require (via the propTypes object) and the library takes care of making sure of warning you if these values are missing.
2. No need to go through multiple hoops to **get your values from your services to your view**. This means you can simply get the values in components instead of passing from Service to Controller to Directive.
3. **No $digest or $apply**. Honestly, i have wasted way more hours than i&#8217;m willing to admit wondering why my values weren&#8217;t appearing in the view, only to discover i was missing an $apply call. In Vue.JS, your bindings *simply work*™.
4. **Amazing tooling**. With [vue-loader](https://github.com/vuejs/vue-loader), it is embarassingly easy to get a setup with hot code reloading, library reload and a bunch of other stuff. Forget the need to get an efficient setup with Gulp or Grunt.
5. **ES6 syntax out of the box**. Coding with ES6 + Angular with Babel always felt very awkard to me, as Angular 1.x wasn&#8217;t built with ES6 in mind. In Vue.JS, on the other hand, ES really empower you to do more with less code, with all the new syntactic sugar like string interpolation and object destructuring. Never learnt ES6? Check out its features at http://es6-features.org/!

# Wrapping up

These 5 features are already more than enough for me to seriously consider Vue.js as my next favorite library. Unfortunately, being too new, Vue.js still does not have the same community modules as Angular or React, what makes a lot of difference. That said, i am really looking forward to contribute to this amazing project and eager to create a lot of stuff with it, and you should be too! [Get started with Vue.js now](https://vuejs.org/guide/index.html)!
