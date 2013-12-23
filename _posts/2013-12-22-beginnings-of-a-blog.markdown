---
layout: post
title:  "Beginnings of a Blog"
date:   2013-12-22 18:00:00
---

Now I'm going to go into a little more detail on what went into getting to where I am right now. I'll explain
things enough to understand how I got there, but many of these I'm only beginning to scratch the surface on
what they do. 
(Here are some examples of the current state: 
[1]({{ site.url}}/images/NewHomePage.png) 
[2]({{ site.url}}/images/NewPostPage.png))

Some of the basics for my development set-up:

 *  MacBook Pro running OS X 10.9
 *  Standard OS X Terminal (with [Solarized Dark Theme][solarized])
 *  [Mac Vim][mvim] (with [Solarized Dark Theme][solarized]) for text editing
 *  [Homebrew](http://brew.sh) for my package manager
 *  Chrome for previewing the site

<img src="{{ site.url }}/images/DevelopmentOverview.png" alt="My development environment" style="width: 625px;"/>


**Make a website**

I would say that 80% of the work you see here was done in a few commands.
Using [Bundler](http://bundler.io), which is a Ruby gem package manager, I created a Gemfile with a couple 
lines


```
source 'https://rubygems.org'
gem 'github-pages'
```
and ran the command `bundle install`. This installs all the gems you specify in the Gemfile as well as any 
dependencies those gems might have. The gem 'github-pages' will install Jekyll for you as well as anything 
else you might need. While installing Bundler and making the Gemfile might be a little more work, it makes 
updating any of the gems much easier as well as transporting your repo to another working directory.

Once [Jekyll](http://jekyllrb.com) is installed, you can just run the following on your terminal to make a 
blog!

{% highlight bash %}
jekyll new myblog
cd myblog
jekyll serve
{% endhighlight %}
This can be accessed on http://localhost:4000 and you get basically everything you see here (or if you're 
from the future, in the screen shots provided earlier in the post).

What Jekyll does is create a static web page without having to create individual HTML files. It uses layouts 
and text files in some kind of markup language (the default is Markdown) and generates the rest of the HTML 
for you.
 
Jekyll does some pretty cool things other than just generating the web pages. One feature I've been using as 
I write this post is how it interacts with drafts. With the `serve` command, you can include the flags 
`-w`, which regenerates the web page whenever any of the files are updated, and `--drafts`, which includes 
any posts that are also in your `_drafts` directory. This allows for easy proofreading since all my changes 
in the draft goes straight to the browser without running any additional commands.

*Why Static Webpages?*

While this is probably worth a whole post, I can address the basic reasons now.
    
The main draw of static web pages is that they are fast. Since there is no server-side processing, 
serving static pages up takes less resources than dynamic pages and allows for the snappiness that a lot of 
people look for in internet browsing. Static web pages aren't always the answer, but for a blog where most 
or all the content will be driven by me, it is great. It is also much cheaper for me to host!


**Find somewhere to host it**

My main requirement right now for a host, since this is just starting and who knows where it'll be in the 
future, is to be as cheap as possible. Since I'm using Jekyll, [GitHub Pages](http://pages.github.com) seems 
like a great fit. GitHub pages has Jekyll support built in. If you name your repository correctly 
(`<username>.github.io`) and commit your source Jekyll directories to it, GitHub does the rest.

Here's a [link][myrepo] to the repository for this site.

If this becomes a successful project, something.github.io is not a catchy *or* professional domain name, 
especially if it becomes my personal blog, so I'll probably have to move it somewhere. I am looking into 
Amazon S3 hosting, which is great for personal website hosting. It also has scalable solutions if you 
suddenly get more traffic.

**Learn how to use Git**

Previous to this project, I had used source control of other types, but all of them had graphical interfaces 
so Git on the command line is something new. I took a couple hours to familiarize myself with how Git works 
at the beginning of this project. 

While Git is mostly spoken for in all corners of the internet at this point, I do think there is one point 
worth making that my silly, 
uninformed brain had thought that other people who are less familiar with source control might think: Git is 
not just GitHub. Actually, Git is not really GitHub at all. GitHub is just a public remote Git repository. 
In the most basic form of source control that Git can implement, there is a local repository Git manages 
that can keep track of all your changes. And then there's remote repositories you can use too, whether it's 
your own private server or GitHub. There are many situations where uploading your project to GitHub wouldn't 
really be necessary. So local Git would do just fine. Git Git Git. Git. (Is there enough of the word 
[Git](http://en.wikipedia.org/wiki/Semantic_satiation) in that paragraph?)

In case you're curious, here's the two sites I used to help me learn Git: [Try Git][trygit] and [Git Immersion][gitimm].

**Begin to get used to Markdown**

[Markdown][mdown] is the markup language that Jekyll uses by default to convert text documents into HTML. 
I have no experience with any kind of markup that would be used in conjunction with Jekyll, so I just went 
with the default. I'll probably look into it eventually and make a full post about it.

Here's an example of some Markdown code (which is done in screenshot form so that you can also see the text 
highlighting)...

<img src="{{ site.url }}/images/MarkdownExampleVim.png" alt="Markdown Example in VIM" style="width: 580px;"/>

... and this is what it produces.

<img src="{{ site.url }}/images/MarkdownExampleChrome.png" alt="Markdown Example in Chrome" style="width: 580px;"/>

**Figure out a way to customize images**

In the [previous post]({{ site.url}}/2013/12/16/hello-world.html) (and this post), I wanted to add images of 
the site in its current state since it will be changing a lot and I wanted a point of reference. The standard
 Markdown solution
  
```
![Alternative Text](image URL)
```
 
ended up not being sufficient. It displayed the images at full scale, which was way too big. After 
researching a couple of solutions (mostly involving implementing other markup languages or using CSS), I 
found out you can insert normal HTML code into Markdown and it'll process it. So I went ahead and added the 
HTML

{% highlight html %}
<img src="{{ site.url }}/images/NewHomePage.png" alt="New Home Page" style="width: 540px;"/>
{% endhighlight %}

and that fixed the problem! This is a pretty great feature of Markdown because anything it can't do, I can 
implement the formatting in HTML. And I only need to implement the minimal amount of HTML required. I 
imagine that this will be useful in a few situations.

**Conclusion**

And here we are! This is really all the information you need to get to where the website is right now. I 
didn't get into everything that I had to do or exactly how everything works, but as I said before, many of 
these tools I'm just getting used to and I would hate to convey some incorrect information.

Hopefully the next post will be after some much needed customization.


[solarized]: http://ethanschoonover.com/solarized
[mvim]: https://code.google.com/p/macvim/
[trygit]: http://try.github.io/levels/1/challenges/1
[gitimm]: http://gitimmersion.com/
[mdown]: http://daringfireball.net/projects/markdown/
[myrepo]: https://github.com/josephlind/josephlind.github.io
