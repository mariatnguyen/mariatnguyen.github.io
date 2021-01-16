---
layout: post
title: Retrieve all WordPress posts faster
categories: [CMS, API]
---

I wanted to build an API that could GET all posts, in the most concise way possible. 

For a little more context, my posts, hosted on WordPress, would be displayed on another domain. 

I originally used the [WordPress REST API](https://developer.wordpress.org/rest-api/). The default endpoint at <b>/wp-json/wp/v2/posts</b> returns 10 posts per page. An older API exists (admin-ajax.php), but that's long been proven to be less reliable and also slower since more of WordPress is loaded. 

The WordPress REST API allows 100 posts per page maximum, with an added parameter. Retrieving all recent 100 posts using the endpoint <b>/wp-json/wp/v2/posts?_embed&per_page=100</b> took a whopping 6.25 seconds to display on the other domain, as shown in the network tab. That's long enough for me to take my cursor over and exit out of the browser after waiting a couple more seconds!

![6.25 seconds](/images/posts/jan2021/625s.png)

It makes sense. The JSON object is 1.2 MB. It's 100 posts of mixed content, including image URLs, blocks of text, and links. There's bloat from the little details down to the dimensions of each featured thumbnail. 

If you dig into the documentation [a little more](https://developer.wordpress.org/rest-api/using-the-rest-api/global-parameters/), you can change the way the API handles its request/response using parameters that cut down the size. For example, you can selectively choose which fields to add using the _fields query parameter. 

However, using the WordPress REST API can still restrict you in some ways. Again, you're only allowed 100 posts maximum. There's also extra, redundant data within the objects - still a lot of bloat.

I created a PHP file that would loop through all post items, and contain only the basic, surface-level object properties that I needed. If I wanted to display just enough to create basic tiles, I'd loop through the id, title, and image.  

Here is my code to loop through posts: 
<div class="blockcode">
<p>$query = new WP_Query( array( 'post_type' => 'post' ) );<br>
$posts = $query->posts;<br>
<br>
$result = [];<br>
foreach($posts as $post) {<br>
   $result[] = array(<br>
      'id' => $post->ID,<br>
      'date' => $post->post_date,<br>
      'slug' => $post->post_name,<br>
      'title' => $post->post_title,<br>
      'excerpt' => $post->post_excerpt,<br>
      'thumbnail' => get_the_post_thumbnail_url( $post_id, 'small' ),<br>
   );<br>
}<br>
<br>
print_r( json_encode($result));</p>
</div>

You won't need your theme and other WordPress includes for this page. <b>SHORTINIT</b>, and other parts of this snippet, will help you load a very minimal version of WordPress.

To strip and modify the default settings, I added this to the beginning of my PHP code:
<div class="blockcode">
<p>define('WP_USE_THEMES', false);<br>
ini_set('html_errors', 0);<br>
require_once('./wp-load.php');<br>
define('SHORTINIT', true);<br>
</p>
</div>

After modifying my GET request to direct to my new API, it only took 1.19 seconds to load. 

![1.19 seconds](/images/posts/jan2021/119s.png)

It loaded in one blink of an eye - 80% faster than the original REST API. 

Creating my own entry point allowed for much more control and a faster connection. 