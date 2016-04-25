# New blog post template

Drop a new `YYYY-MM-DD-myawesomepost.markdown` into `/source/_posts` and images into `/source/images`

**Note: date in the post needs to be yesterdays date in order to appear*
 - Future dates can be set if you want post to appear in the future
 
## Post Template Example

```
---
layout: post
title: 'My awesome blog post'
date: 2016-04-22                # Needs to be yesetdays date to appear
author: Glyn Hudson
comments: true
categories:                     # LOWER CASE
- awesome
- blog
- post
---

Insert some awesomeness here. Full markdown supported

Use this tag with a new line space above and below to define how much of the post is shown on the blog front page before a *Read More* button to view the full post

<!--more-->

Yes more awesomeness

Insert an image which will get scaled to fit the page (responsive)

![image](/images/image.png)

Insert an image of fixes size e.g. 400 px

{% img /images/image.png 400 %}

```php
PHP code with hilighting

```
cpp, python and console supported and [many more](http://coapp.org/reference/garrett-flavored-markdown.html#cod)

```