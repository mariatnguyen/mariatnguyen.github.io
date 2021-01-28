---
layout: post
title: Creating a class named Cat
categories: [Javascript, Objects]
---

A class is a function used as a template for creating objects. It is one of Javascript's data types, and is part of what makes Javascript an object-oriented programming (OOP) language.

Let's say I wanted to create cats within my program, but I wanted multiple kinds of cats with various characteristics, abilities, and names. I could create arrays or nested arrays with this data, but I could also take advantage of classes. 

Classes are meant to be reusable and scalable, so if an alley cat happens to wander in my space and I decide to keep him, I can easily fit this anonymous kitty in. 

The class function is declared using the "class" keyword, and always requires a "constructor" method – no more than one constructor method and no less than one. Otherwise our cats would all go missing!

Unlike other function declarations, you need to declare your class first to use it. Class expressions are another way to introduce a class function, but here I will be declaring the class.

<div class="blockcode">
<p>class Cat {<br>
&emsp; &emsp;constructor(name,birthday) {<br>
&emsp; &emsp; &emsp; &emsp;this.name = name;<br>
&emsp; &emsp; &emsp; &emsp;this.birthday = birthday;<br>
&emsp; &emsp;}<br>
}
</p>
</div>

Classes can contain properties and methods beyond the constructor method. 

Let's add some more functionality to the cat object.

<div class="blockcode">
<p>class Cat {<br>
&emsp; &emsp;constructor(name,birthday) {<br>
&emsp; &emsp; &emsp; &emsp;this.name = name;<br>
&emsp; &emsp; &emsp; &emsp;this.birthday = birthday;<br>
&emsp; &emsp;}<br>
&emsp; &emsp;meow() {<br>
&emsp; &emsp; &emsp; &emsp;alert('Meow!');<br>
&emsp; &emsp;}<br>
}
</p>
</div>

I've added a simple alert function. All cats meow, purr, chatter, and/or have some way of communicating with their surroundings, so this universal method for a cat makes sense.

Cats are funky creatures. Sometimes cats are consistent, and we could add on basic methods to what we have so far. Here's a few more ideas:<br>
• scratch()<br>
• eat()<br>
• vomit()<br>
• sleep()<br>
• nap()<br>
• runAroundForTenMinutesStraight()<br>

<p style="text-align:center;"><img src="/images/posts/jan2021/cat.png" alt="meow" width="600" height="auto"></p>

Now, let's add more cats.

Inheritance is another reason why Javascript is an OOP language. Inheritance offers the ability for a class to inherit all methods from another class.

To create a class inheritance, you can use the "extends" keyword when declaring the new child class. The super() method is used to refer to methods from the parent class.

<div class="blockcode">
<p>class Bombay extends Cat {<br>
&emsp; &emsp;constructor(name,birthday,color) {<br>
&emsp; &emsp; &emsp; &emsp;super(name);<br>
&emsp; &emsp; &emsp; &emsp;super(birthday);<br>
&emsp; &emsp; &emsp; &emsp;this.color = color;<br>
&emsp; &emsp;}<br>
}<br>
var MrFuzzy = new Bombay("Mr. Fuzzy", "January 27, 2020","Black");
</p>
</div>

Some breeds have particular characteristics. In this case, bombay cats are characterized as being very friendly and active. They have unique physical features like having yellow or green eyes and a shiny black coat. We could continue including more methods to this Bombay class. 

If I were programming my cat act as he always does, I'd add a conditional statement to .meow() everytime his food bowl was empty. 

We could also continue making a Calico, Tabby, American Shorthair, etc class to extend the Cat class. 

I could proceed discussing the construction of a cat for as long as my cat chases his own shadow, but I think I'll stop here. There you have it! A simple Cat class.