---
layout: post
title: "Detect mobile - tablet orientation using jquery"
date: 2014-08-01 22:34:42 +0800
comments: true
categories: 
---

This Javascript / Jquery code can detect mobile or tablet orientation.

<pre>
	window.addEventListener("orientationchange", function() {
		var orientation = window.orientation;
      }, false);
</pre>

a portrait orientation will result of a value of "0" while landscape orientation will yield a result of "0" this is helpful if you are creating a realtime orientation query.

<small>tags: javascript mobile orientation, javascript tablet orientation, device orientation jquery, jquery window orientation</small>