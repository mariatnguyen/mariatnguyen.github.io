---
layout: post
title: Best way to order your CSS properties?
categories: CSS
---

Overtime, I've learned to respect the beauty of a well-organized, neat style sheet. It's attractive when there's an even amount of tab characters, the multicolored lines are consistent, and I barely have to use CTRL + F. 

In a way, a good style sheet is like a clear instructions manual. CSS, Sass, LESS, or Stylus are instructions to tell web elements how they'll render on the page. 

The style sheet should first flow well on the surface. The organization of your selectors should make sense and the style sheet should similarly reflect the DOM, addressing elements from top to bottom, general to specific, and largest to smallest. 

When I was just starting out and tinkering with code, it was straightforward for me to simply append everything to the end. I'd add the elements themselves to the end of an external style sheet and write in properties at the end of each element, as I went along. Looking back, it feels deviant to do that now. I'd eventually need to make revisions to it. My previous method would get ugly and inconvenient within a short amount of time; it would be harder to manage and everything would generally just appear to be in random order. 

There is no widely known convention to ordering CSS properties. According to [this](https://css-tricks.com/poll-results-how-do-you-order-your-css-properties/){:target="_blank"} poll on css-tricks.com, 39% of developers randomly arrange their properties with no specific plan. The majority of people do not follow a convention based on property type, and instead group their CSS properties randomly, by line length, or alphabetically.

Some people who do like a level of order to their style sheet might keep the [CSS box model](https://www.w3schools.com/css/css_boxmodel.asp){:target="_blank"} in mind when organizing CSS properties. The basic box model considers all elements to be a calculated whole sum, where the border, margin, and padding follow the actual content. 

A portion of developers might subscribe to the [concentric CSS](https://rhodesmill.org/brandon/2011/concentric-css/){:target="_blank"} method, which starts outside the box model and moves inward — layer by layer. In this case, the dimensions of your object come after things like margin, outline, and background. 

The CSS box model convention and concentric CSS way of coding both follow the idea of viewing an element as a box with both an inside and outside. However, both practical approaches are different in outcome. 

The way I prefer to prioritize my properties surrounds the idea of building an element. I consider what properties are most important and influential to the element's construction. Additionally, I group by type. 

In theory, how important a property is can be subjective to the element. An element's purpose could be vastly different from its parent, children, and sibling elements. When I use the word "important," I mean to say that the content is meant to be the focus and all properties surrounding the content are meant as decorations. 

My personal order is:<br>
• Display<br>
• Position and layout<br>
• Box model properties<br>
• Visual properties<br>
• Text properties<br>
• Other<br>
• Animations

If I have an element that I'm looking to style, the display property of the element is the most important to me. The default display for most elements is block or inline. What if the element is initially hidden? What if it needs to be displayed as a flexible item with each child element being a column? This entirely changes the look of it. 

After considering where this element is in relation to the page, and how big it is, other box model properties are declared, respectively. Everything complimentary like the background color and text color will succeed. 

Within the groups themselves, I follow the same method of considering which properties are most pertinent.

Here it is in action: 

<div class="blockcode">
<p>.element {<br>
&emsp; &emsp;<span class="blockcomment">/*Display*/</span><br>
&emsp; &emsp;display: block;<br>
&emsp; &emsp;<span class="blockcomment">/*Position and Layout*/</span><br>
&emsp; &emsp;position: absolute;<br>
&emsp; &emsp;z-index: 1;<br>
&emsp; &emsp;top: 0;<br>
&emsp; &emsp;right: 0;<br>
&emsp; &emsp;<span class="blockcomment">/*Box Model Properties*/</span><br>
&emsp; &emsp;width: 100px;<br>
&emsp; &emsp;height: 100px;<br>
&emsp; &emsp;min-width: 100px;<br>
&emsp; &emsp;min-height: 100px;<br>
&emsp; &emsp;margin: 10px;<br>
&emsp; &emsp;padding: 10px;<br>
&emsp; &emsp;border: 1px solid #000;<br>
&emsp; &emsp;<span class="blockcomment">/*Visual Properties*/</span><br>
&emsp; &emsp;background-color: #f0f0f0;<br>
&emsp; &emsp;<span class="blockcomment">/*Text Properties*/</span><br>
&emsp; &emsp;font-family: Helvetica, Arial, sans-serif;<br>
&emsp; &emsp;font-size: 12px;<br>
&emsp; &emsp;line-height: 1em;<br>
&emsp; &emsp;text-align: left;<br>
&emsp; &emsp;text-transform: uppercase;<br>
&emsp; &emsp;<span class="blockcomment">/*Other*/</span><br>
&emsp; &emsp;cursor: pointer;<br>
}
</p>
</div>

After I've "built" my element, pseudo-classes and pseudo-elements like :hover and :before would be added after the regular selector. 

Optimizing your style sheet may be more important in settings where the code is meant to be reusable and passed around. Consistency and a clear order could greatly add to readability. 

If you're working with a preexisting style sheet, it may be better to follow conventions that lie within the sheet already. 

Ultimately, putting certain properties before others won't speed up your page. There is no right or wrong way to organize your properties in the eyes of a browser. Either way, your style sheet will still be rendered the same no matter how your properties are arranged. 

The "best" way to order your CSS properties could equate to what is most comfortable to you. Whether you're coding for yourself or on a project, it is all about personal preference and what flows right to your eyes. 