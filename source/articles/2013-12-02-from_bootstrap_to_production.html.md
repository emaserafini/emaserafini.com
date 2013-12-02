---
title: From bootstrap(3) to production
date: 2013-12-02
tags: example
---

Twitter Bootstrap is based on Less.js, the popular dynamic CSS scripting language. In your Rails project you may prefer to use Sass instead of Less, because it’s already supported by Rails out of the box, or because your application already contains a large amount of Sass code, or possibly just because you’re more familiar with it. At first glance, this seems to be a serious problem for Twitter Bootstrap: it’s not appropriate for a large portion of the Rails community that prefers Sass, since it was implemented with the Javascript-centric Less.js technology.

### Stylesheets

[Sass-twitter-bootstrap](https://github.com/jlong/sass-bootstrap) is not a gem, but instead is just a github repo containing Twitter’s translated code. To use it in your Rails app, just clone the repo and copy Sass source files right into your application like this:


	$ git clone https://github.com/jlong/sass-twitter-bootstrap.git

	$ cp -r sass-twitter-bootstrap/lib path/to/app/assets/stylesheets/twitter


And now since the Rails asset pipeline supports Sass out of the box, we’re good to go… almost! If you run your app now, you’ll see an error:


	ActionView::Template::Error (Undefined variable: "$baseline".
  	(in /path/to/app/assets/stylesheets/twitter/forms.scss))

To fix this, there’s a simple solution remove line ``*= require_tree .`` from `` application.css``. The problem is caused because the translated Sass version was designed to be included once using the bootstrap.scss file, which in turns includes all of the other files.

### Javascripts

### Font

### Production setup