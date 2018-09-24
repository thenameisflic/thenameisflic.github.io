---
id: 75
title: "The Angular thumbnail grid you&#039;ll love"
date: 2016-03-18T19:31:02+00:00
author: flic
layout: single
guid: http://www.thenameisflic.com/?p=75
permalink: /the-thumbnail-grid-youll-love-and-heres-how-i-did-it/
categories:
  - angular
  - bower
---

Recently i&#8217;ve been reading a lot about [how much carousels suck](http://shouldiuseacarousel.com/). Still, all of the alternatives i&#8217;ve found wouldn&#8217;t fit very well for my personal portfolio. By a bit of serendipism, i&#8217;ve stumbled upon an [article on Codrops](http://tympanus.net/codrops/2013/03/19/thumbnail-grid-with-expanding-preview/) teaching how to create a thumbnail grid just like [Google Images](https://www.google.com.br/search?q=kittens&safe=active&source=lnms&tbm=isch&sa=X&ved=0ahUKEwjU__eS4MrLAhXJFpAKHYSHDDAQ_AUIBygB&biw=1301&bih=683#safe=active&tbm=isch&q=rainbow+kittens). And in my brief user testing, it worked pretty well!

<div id="attachment_77" style="width: 930px" class="wp-caption aligncenter">
  <a href='http://104.236.4.255/wp-content/uploads/2016/03/ng-thumbnail-grid.png'><img class="wp-image-77" src="http://104.236.4.255/wp-content/uploads/2016/03/ng-thumbnail-grid-300x156.png" alt="" width="920" height="480" /></a>
  
  <p class="wp-caption-text">
    Pick an interesting thumbnail, click on it&#8230;
  </p>
</div>

<div id="attachment_78" style="width: 924px" class="wp-caption aligncenter">
  <a href='http://104.236.4.255/wp-content/uploads/2016/03/ng-open.png'><img class="wp-image-78" src="http://104.236.4.255/wp-content/uploads/2016/03/ng-open-300x158.png" alt="angular-thumbnail-grid-closed" width="914" height="480" /> </a>
  
  <p class="wp-caption-text">
    &#8230; and you get a full screen preview!
  </p>
</div>

As my website uses Angular, it would be very useful to have a directive to make it easier to integrate. As i couldn&#8217;t find one, i made one!

[Grab it on Github!](https://github.com/flicsl/angular-thumbnail-grid.git)
