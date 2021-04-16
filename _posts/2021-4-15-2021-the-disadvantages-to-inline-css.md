---
layout: post
title: The Disadvantages of Inline CSS
categories: CSS
---

There are several downsides to implementing unique styles within an HTML element. Some may even consider inline CSS to be bad practice. 

Here are just a few disadvantages:


1. Hard to keep track of

From the surface, the page is likely styled using one or more stylesheets. Inline CSS is not always expected and therefor could be harder to find. Programmers may have to search for every instance of "<style="..."" instead of defaulting to looking through stylesheets.


2. Not reusable

Inline CSS can be harder to manage. If you're adding styles right within the HTML element, you can't reuse the styles anywhere else - which could inconvenience you in the future if you're looking to add the same styles again. For consistency's sake, making the same type of button a gray color will need to done throughout the page and throughout the whole site. It doesn't keep the DRY (Don't repeat yourself) principle in mind. To this point, stylesheets help reusibility and consistency. 


3. Load time

CSS stylesheet files are cached via client-side browser cache. This makes load time really helpful. Unlike scripts and stylesheets, HTML isn't always cached unless you take advantage of it and set it to do so - and even so, it is sometimes recommended to not cache HTML as your page content may always be shifting. When you have inline styles that are not cached, that portion will then always load that snippet which adds to the overall payload of your page.


4. Specificity

Specificity is the notion that if there are conflicting styles, the browser will follow particular rules on which style will show up to a user. Inline CSS is typically the dominant style since it has the highest specificity second to the "!important" rule. This means that inline CSS will almost always override what is being displayed. 


5. Readability

The HTML markup will not be as smooth and can be harder to parse manually. 


6. Pseudo-elements and Pseudo-classes

You won't be able to style pseudo-elements and pseudo-classes with inline styles, since they are abstractions of the DOM. You can only modify HTML elements already on the page. This leaves the page looking more static and with less power in your hands, since you won't be able to specify things like :hover or ::after. 


<div class="blockcode">
&lt;p style="font-size:20px;font-weight:bold;text-transform:uppercase;"&gt;We're gonna have to do a lot of copy and pasting...&lt;/p&gt;
</div>


There are valid use cases for inline CSS. One of my most common uses for inline CSS is if I need to toggle or add overriding styles when using Javascript. Another use would be if I was creating a single page that requires little complexity, and could potentially be more cumbersome if I added stylesheets.  

All in all, inline CSS is a powerful tool with particular upsides and downsides. 
