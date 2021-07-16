---
layout: post
title: "Hugo vs. Jekyll: Which is Right for Your Blog?"
description: Hugo and Jekyll are two of the most popular static site generators.
  This comparison explores the main features of both.
categories: platforms
author: john
date: 2021-04-06T08:43:43.718Z
img: /assets/posts/hugovsjek-20.png
cta: Content Ideas
---
Static site generators create HTML sites, with predictable page layouts and content with regular presentation such as blogs. There are many frameworks that can leverage a programming language and allow you to reuse code and process assets for these HTML pages, but this article will compare two of the most popular: [Hugo](https://gohugo.io/) and [Jekyll](https://jekyllrb.com/).

## Why Use Static HTML Pages?

Static site generators are appealing because they produce secure sites requiring little maintenance that are faster to serve than dynamically generated web pages. With dynamic web pages, a web framework installed on a server generates the page a user sees. A user makes a request, the server queries a database, pulls out the information users want to see, combines that data into an HTML page, then sends that page to a user. 

With static HTML pages, the pages are pre-rendered, so the server doesn’t do any of the work of building the page. It only handles sending the appropriate page to the user. This means that static HTML pages are faster, and the computing requirements for the server are much smaller; important in cloud environments where you’re charged for computing power.

Static pages cut out the page generation, so the user receives their page much more quickly. Security risks are also smaller because there are fewer moving parts for attackers to infiltrate and exploit. Static HTML pages are easily cached, so they’re well suited to be served from content delivery networks (CDNs), making response times even faster.

Because static pages don’t require servers to perform calculations or query the database, you can deploy them using very simple, low-cost hosting options like an [Amazon S3 bucket](https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html) or [GitHub Pages](https://pages.github.com/).

<!-- signup -->

## Static Site Generators

You could simply write an HTML page and put it on a server, hearkening back to the [early days](http://info.cern.ch/hypertext/WWW/TheProject.html) of the web, but static site generators make it much easier to create new pages that use existing templates or modify all of your existing pages at once.

One of the first static site generators to restart this trend in web development was Jekyll. Hugo joined in five years later.

## Hugo vs. Jekyll

With either generator, you can get a templated blog up and running in under thirty minutes. If you’re starting from nothing, Hugo is slightly easier to install. With Jekyll, you have to install a [couple prerequisites](https://jekyllrb.com/docs/installation/#requirements) like Ruby. Go comes as a precompiled binary bundled along with the Hugo installation.

For both frameworks, you’d normally write a content file like a blog post in HTML or Markdown. This content gets combined with HTML templates, which wrap and style the content, outputting an HTML file for display on the web.

Both frameworks allow developers to add variables to content, using the YAML markup language, and consume data files in common formats like JSON and CSV. Both frameworks also come with a number of features useful for a blog, like tags and the ability to route content files to finished HTML pages. They are also open source, so you can request changes and [contribute](https://jekyllrb.com/docs/contributing/) [improvements](https://gohugo.io/contribute/development/).

The first and most fundamental difference between the two frameworks is the language they’re written in. Jekyll is written in Ruby, a popular scripting language that was one of the first languages to come with an opinionated web framework, making it extremely popular for building websites quickly. Hugo is written in Go, which was developed at Google with an eye on concurrent execution, optimizing for deployment in cloud environments where computing power is distributed across many machines. 

Each framework also has different preferences about what languages it works well with. Jekyll offers support for [CoffeeScript](http://coffeescript.org/) and SASS/SCSS. Hugo supports TOML and JSON markdown in content files, but supporting SASS and SCSS might require [some additional setup](https://gohugo.io/troubleshooting/faq/#i-get-tocss--this-feature-is-not-available-in-your-current-hugo-version).  

![The Jekyll framework](https://imgur.com/DsSqC7u.png)

### The Template Situation

One of the main benefits of Jekyll is its ease of use, well-developed documentation, and broad support from major organizations like GitHub. Jekyll was released twelve years ago and helped kick off the new interest in static HTML sites. Hugo was released later and is less popular, so it has a less developed ecosystem of plug-ins and templates.

GitHub topics offers a whopping [1,200 themes](https://github.com/topics/jekyll-theme) to choose from for Jekyll, while there are only 370 options offered on the Hugo [themes pages](https://themes.gohugo.io/) ([although, you can also create your own themes](/learn/creating-hugo-themes)). Obviously, it’s much more likely you’ll find a theme with the look you want with Jekyll. Jekyll is supported by GitHub, so if you want a simple, no-cost deployment, Jekyll works seamlessly with [GitHub Pages](https://pages.github.com/), so you can have a simple blog up and online very quickly by following GitHub’s [excellent documentation](https://docs.github.com/en/github/working-with-github-pages/setting-up-a-github-pages-site-with-jekyll).

Another difference between the frameworks is that creating a brand-new site with Jekyll by running the command `jekyll new my-awesome-site` installs a basic theme, while creating a new site with the `hugo new site my-awesome-site` command only generates the folder structure and an archetype file. With Jekyll, you’ll have something to work with right away, but with Hugo you’ll be looking at an empty screen waiting for you to add a theme or custom templates.

This can be great for a totally customized setup, but Jekyll has a much quicker path to seeing content you can work with.

![First post with Jekyll](https://imgur.com/V8eJrtu.png)

### Speed, More Speed

One of the major benefits of using Hugo [is its speed](https://forestry.io/blog/hugo-vs-jekyll-benchmark/). Leveraging the focus on concurrency of the Go language means blogs with thousands of entries or tons of images will generate HTML more quickly. That matters if you’re running code anywhere you’re paying for computing power.

It also matters during development, because changes that you make to templates or content are re-rendered more quickly with Hugo. This speed difference is noticeable even at low page counts, but it becomes significant if you’re building a hundred pages of content.

![The Hugo framework](https://imgur.com/3OihlRh.png)

### Hugo Bonuses
Hugo offers support for internationalization, providing multiple ways to categorize content in different languages. Hugo also offers image processing, built-in menus, site mapping, and live reloading.

You can achieve the same result in Jekyll, but it’ll take more work to set up. In Jekyll, this functionality comes from plug-ins, but if you’re building complicated pages, it’s nice to have it built-in.

### Hosting

Both languages offer options for easy hosting, but Jekyll is the simplest. Jekyll and GitHub Pages have a close, long relationship, and deploying a Jekyll project to GitHub Pages is simple and fast, which can be a great option for trying out a blog.

Hugo also offers many hosting options. For both generators, you have two fundamental options:

1. You can run the site generator locally, then upload the results to a server. You can do this manually or instruct some service to grab your updated HTML.
2. You can install the static site generator on a computer in the cloud, tell that computer to run the content generation command, then serve the files that process creates. This is how services like [Amazon Amplify](https://aws.amazon.com/amplify/hosting/), [CloudCannon](https://cloudcannon.com/), and [Netlify](https://www.netlify.com/) all work. These providers all have specific guides for deploying sites, but the deployment process is pretty painless when using either static site generator.

## What to Choose

Jekyll and Hugo are both well suited for blogs and other frontend-oriented sites. They generate static HTML pages by combining content written in a markdown language with HTML templates.  

Jekyll has the fastest setup, more options for templates, and offers an easier experience when getting started, but it can start to feel slow once you’re processing a hundred pages. Hugo's initial setup is more complicated, but it can handle larger sites with more speed.

When deciding, think about the languages you’re familiar with, the types of markdown you want to use, and how you’ll deploy the site. If you want to start blogging right away, Jekyll is a great fit, but if you anticipate writing lots of content, the speed and features of Hugo will make your development experience smoother.
