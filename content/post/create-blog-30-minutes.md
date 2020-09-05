---
title: "Create your own blog in 30 minutes using Hugo, a static site generator written in Go"
date: 2019-08-06T17:18:26+05:30
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
thumbnailImage : img/thumbnail/hugo-blog.jpg
coverImage: img/cover/hugo.png
coverMeta: out
metaAlignment: center
---
Do you know you can create your blog without any knowledge of content management system or actual knowledge of creating a website, setting it, styling it or improving it? Well, you can with the world’s fastest framework for building websites that is [Hugo](https://themes.gohugo.io)

Before going forward it is suggested that you must have an account on [Github](https://github.com) for hosting your blog.

## Why Hugo?
* Hugo is the fastest tool of its kind. At <1 ms per page, the average site builds in less than a second.
Hugo supports unlimited content types, taxonomies, menus, dynamic API-driven content, and more, all without plugins.

* Hugo shortcodes allow for both beauty and flexibility.

* Hugo ships with pre-made templates to make quick work of SEO, commenting, analytics and other functions.  One line of code and you're done.

* Hugo provides full i18n support for multi-language sites with the same straightforward development experience Hugo users love in single-language sites.

* Hugo allows you to output your content in multiple formats, including JSON or AMP and makes it easy to create your own.

* Because there is no database, no plugins requiring any permissions, and no underlying platform running on your server, there's no added security concern.

* Version control is easy. Some CMS platforms use their own version control system (VCS) or integrate Git into their interface. With Hugo, all your source files can live natively on the VCS of your choice.

## Install Hugo

##### Mac OS

>`$ brew install hugo`

##### Windows

> `$ choco install hugo -confirm`

##### Linux
> `$ snap install hugo`

There are many other ways of installing from GitHub repository, you can check them [here](https://gohugo.io/getting-started/installing/)

## Create a new site

Create a new site that will become your blog

> `$ hugo new site myblog`

Change into the newly created directory

>``$ cd myblog``

Project will somewhat look like this
![Project skeleton](/img/create-blog-30-minutes/blog1-pic1.png)


## Clone Theme

With Hugo you can create your theme however here we will use [Hugo-geo](https://themes.gohugo.io/hugo-geo/) as an example of them.

> `$ cd themes`

> `$ git clone https://github.com/alexurquhart/hugo-geo.git`

If you do not have git installed on your system then you can download .zip file from [Github](https://github.com/alexurquhart/hugo-geo.git) and extract this repository and copy it in the themes directory.

## Start Theme

Start this theme by copying the content of config.toml of the theme to your config.toml.
You can verify whether it is activated by hugo server 

> `$ hugo server -D`

Now in your browser go to http://localhost:1313 and bam!!! Here’s what your website will look like.
![website look](/img/create-blog-30-minutes/blog1-pic2.png)

## Updating your blog

Updating your config.toml file will lead you updating your website such as :

* Adding your profile picture

* Updating your contact details

* Updating your page contents

* Adding Disqus shortname and google analytics


## Add content to your blog

Adding content to the blog is very simple.


> `$ hugo new post/hello.md`

![content](/img/create-blog-30-minutes/blog1-pic3.png)
![content](/img/create-blog-30-minutes/blog1-pic4.png)

.md files support markdown format. If you want to learn about markdown format [click here](https://www.markdownguide.org/).

## Host your blog

Here we will host our website on Github pages.

1. Create a repository of name `username.github.io` where username is your Github username

2. Clone this repository to your system by ``git clone https://github.com/username/username.github.io``

3. Send your Blog data to your repository by ``hugo -d ../username.github.io/``

4. ``git add .``

5. ``git commit -m"Initial commit"``

6. ``git push origin master``

***Congratulations!!*** you now have your own website.