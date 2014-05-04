---
layout: post
title: "Parallax scrolling"
date: 2014-04-07 18:27:59 +0800
comments: true
categories: 
---


Today I created a Simple Parallax Scrolling that scrolls different elements with different speed upwards, at first it looks intimidating but its simple to create probably the most challenging part of the parallax is how you can make it scroll smoothly, but you can achieve it by using some plug-ins
These are the part of my codes:

Html

<pre>
&#60;div class="small-clouds-layer">
    &#60;img src="blue-clouds-1.png" class="small-1">
    &#60;img src="blue-clouds-3.png" class="small-3">
&#60;/div>
</pre>


Css

<pre>
.small-clouds-layer{
    position: absolute;
    top: 600px;
    width: 100%;
}
.small-1{
    margin-left: 300px;
}
.small-3{
    margin-left: 300px;
}
</pre>


Javascript

<pre>
$(window).bind('scroll',function(e){
    parallaxScroll();
});

function parallaxScroll(){
    var scrolled = $(window).scrollTop();
    $('.small-clouds-layer').css('top',(600-(scrolled*.5))+'px');
}
</pre>


the javascript code above is enough to make a parallax scrolling if you want to animate more elements just set it's css rules and add that elements inside parallaxScroll function