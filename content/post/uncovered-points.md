---
title: "Uncovered points associated with Hugo"
date: 2019-08-20T01:09:28+05:30
categories:
- blog
- Random discovery
tags:
- hugo blog
- create blog
- go programming language
keywords:
- tech
autoThumbnailImage : false
thumbnailImagePosition : "left"
thumbnailImage : img/thumbnail/blog2.jpg
coverImage: img/thumbnail/blog2.jpg
coverMeta: out
metaAlignment: center
---
In the last article, I tried to cover almost every point required for creating your blog. However, there are still some points left which remain uncovered in the previous section.

This article will cover those points which I feel are not covered in the official documentation or if covered are not much focussed in there quick start guide.

### Point 1
Most of the time I read questions on the internet of people asking that even after creating or copying the config.toml file there project fails to start or if starts it does not work properly.
The solution is very very simple. In many themes of Hugo there occurs a line in config.toml stating ```themesdir = "../.."``` just remove that and check that the name of the theme in the file matches with the name of the directory of the theme which you copied as in the previous article.

See line number 3 in the following image
![Project skeleton](/img/blog2-pic1.png)

### Point 2
The worst problem that I faced with Hugo is this one only. Well, the steps are pretty simple for a new post:

1. `hugo new post/hello.md`

2. Write your content in the markdown format

3. `hugo server` to check your progress on localhost

Now the problem here arises that it will not show your article on your localhost. The reason lies in the line number 3 (see the figure) (Note: line number may vary with theme). It states `draft: true` which means that your post is in draft condition or simply for testing purpose. For checking your draft posts on localhost you can type `hugo server -D` (here -D means --buildDrafts that includes content marked as a draft). Now if you feel satisfied with your post and are now ready to publish it just make `draft: false`.

![Project skeleton](/img/blog2-pic2.png)

### Point 3
In your config.toml file you may somehow encounter with line baseurl = http://example.com/. Correct it by writing your website name, for example, baseurl = https://username.github.io.
![Project skeleton](/img/blog2-pic3.png)

These set of points must help you while writing your blog with Hugo.

Do tell me your opinions on these points. Also, if you feel some other problems while writing your blog with Hugo do let me know I will try to cover them in my upcoming posts.