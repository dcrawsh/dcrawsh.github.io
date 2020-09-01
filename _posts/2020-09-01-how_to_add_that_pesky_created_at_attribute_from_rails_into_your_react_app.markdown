---
layout: post
title:      "How to add that pesky created_at attribute from Rails into your React App"
date:       2020-09-01 21:51:35 +0000
permalink:  how_to_add_that_pesky_created_at_attribute_from_rails_into_your_react_app
---


![](https://d15shllkswkct0.cloudfront.net/wp-content/blogs.dir/1/files/2013/06/monkey-scratching-head.jpg)

So you have a fresh new component created for your new React app...It has a title and content beautifully displayed to the UI. Wouldn't it be nice if there was a date that marked the created or last update to this resource.  You might think you could just easily access that data doing something like 

```<p>{post.attributes.created_at}</p>```

...simply adding it to a paragraph element using JSX. However, this gives you a very ugly looking 2020-08-28T16:08:31.385Z. What the hell is that? Wouldn't you like the classic DD/MM/YYYY?

Well this is called UTC. This stands for Coordinated Universal Time. Your first logical step but be to try something like 

```Date.parse('2020-08-28T16:08:31.385Z')`` 

returns

```1598630911385```

After some searching around you might find that you can easily create a new Date like 

```let newDate = Date('2020-08-28T16:08:31.385Z')```

which returns

"Tue Sep 01 2020 14:39:33 GMT-0700 (Pacific Daylight Time)"

Unfortunatley there is no built-in JavaScript methods to covert this to the short date version we want.  Therefore, you are going to need to write your own method to Change that string...so get to work!


--------------------


or you could use this 

```function railsDateConverter (inputFormat) {
    function pad(s) { return (s < 10) ? '0' + s : s; }
    var d = new Date(inputFormat);
    return [pad(d.getMonth()+1), pad(d.getDate()), d.getFullYear()].join('/');
  }```
	
	



