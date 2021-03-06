---
layout: "post"
title: "Learning Jekyll"
date: "2016-02-27 22:13"
category: jekyll
---
My interest was piqued recently by [Jekyll](http://jekyllrb.com), the blog-aware static site generator. I'm always interested in learning new, interesting technologies, plus I've been thinking about rejuvinating my site for some time, which gave me the perfect excuse to install Ruby and fire it up.

<img src="/images/jekyll.png" class="image fit" />

I'm drawn to Jekyll as it seems to hit a sweet spot for me due to the following features:

### Markdown

I love [Markdown](https://en.wikipedia.org/wiki/Markdown). Markdown is a lightweight markup language with a simple, unobtrusive syntax. It looks great and is easily readable in its plain text form but is also easily converted into HTML. I find that I am using Markdown more and more every day.

Jekyll posts and pages can be written in Markdown format as well as HTML. Markdown is also compatible with HTML, so if you ever get some "widget" code that you want to embed on your site you don't need to convert it in any way - just copy and paste the code in and mix the two together.

### Static site generation

Previously I've used [Blogger](https://www.blogger.com), [WordPress](https://wordpress.org) and [Ghost](https://ghost.org) to manage my site. Blogger and the hosted offerings of WordPress and Ghost are ok, but they just don't give me the flexibility I feel I need to be able to modify my templates and get my site running exactly how I want - there's always some kind of restriction. This led me to hosting WordPress and Ghost myself, which required a LAMP style stack or Node.js on a server somewhere which, while not exactly a problem, was an overhead that I could do without.

Jekyll generates static sites. It processes your pages, posts and templates and produces simple output in the form of HTML files, allowing you to serve them up from almost any kind of web server. [Apache](https://httpd.apache.org), [Lighttpd](https://www.lighttpd.net) and [Nginx](https://www.nginx.com) are all welcome here, or you could just upload your files to an Amazon S3 bucket and serve them directly from there... *Jekyll doesn't care*. Serving static HTML is also highly efficient, though I don't for a second imagine that my site would ever attract enough traffic to cause me a problem.

### GitHub pages

Jekyll is used by GitHub for their [Github Pages](https://pages.github.com) feature. This allows you to create or push a Git repository with your Jekyll site to them, which they will then build and host *for free*. You can use a github.io address or your own domain name. This is perfect for me, as it allows me to develop my site and write content locally whilst being able to maintain it from anywhere with an internet connection. It also means that I don't have to worry about hosting fees, backups or versioning. People can also fork my code and set up their own site easily and they can raise bugs, feature requests and even submit their own fixes & features if they choose to.

### Simple, flexible templating

Jekyll uses the [Liquid](http://liquidmarkup.org) library for templating. This is extremely easy to learn and so far seems fairly capable, especially with the filters that Jekyll supports natively. It has its quirks, but I have not yet come across something which I haven't been able to do.

### Syntax highlighting

Jekyll includes support for syntax highlighting of code snippets, which may come in handy for me, though I will probably lean more towards embedding [GitHub Gists](https://gist.github.com) instead.

## The result

<img src="/preview.jpg" class="image fit" />

After a few evenings reading and coding the result is this site that you're reading right now. I started with the [Strata design](http://html5up.net/strata) by HTML5UP, which comes as plain HTML with CSS and SASS source code (Jekyll can also compile SASS for you, by the way) and converted it into a bunch of templates and supporting files which can be used with Jekyll. You can find the code in my [GitHub repository](https://github.com/DavidForster/strata-jekyll). [CloudCannon](http://cloudcannon.com) already have a version of Strata in their [GitHub account](https://github.com/CloudCannon/Strata-Jekyll-Theme), but it does not offer what I consider the minimum set of functionality I require in a theme and besides that, what better way to learn than to implement everything from scratch?
