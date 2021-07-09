---
layout: post
title: Introduction to Publii, the Static Site Generator
description: Review of the static site generator, Publii
categories: platforms
author: kealan
date: 2021-07-07T19:00:49.467Z
img: /assets/posts/x9eq4oe.jpg
---
There is so much to consider when making a basic website. You have to think about how to get a domain name and where to get it. You need to work out the general costs of building and maintaining it, where you can host your content, and how much the hosting would cost, alongside actually doing the coding and getting all the assets together. You need to performance test it, make sure it is kept up-to-date, and configure a process to get code regularly deployed out. On top of all that, there are web-safety standards like configuring HTTPS instead of HTTP to ensure the connection is encrypted.

This can be confusing and overwhelming—especially if you aren’t familiar with software  development or web development. Static site generators (SSG) were introduced to solve this problem: How do you easily create and maintain a website?

Publii is one such SSG. In this article, we’ll look at the general user experience, and take a high-level overview. We’ll cover some of the pros and cons and discuss who it’s best suited for.

This article is aimed at bloggers or marketers, so you won’t need any advanced developer knowledge to engage.

## What Is a Static Site?

To accurately explain what SSGs actually do, you have to first understand what a static site is.

A *static site* is a site that will load the same way every time. It doesn't greet you with your name or load personalized content. Nothing on the website changes unless the author specifically changes it.

SSGs are normally very non-technical, so coding experience is not essential. The interface is what’s known as a “point-and-click” experience, which means users set things up visually, rather than via code.

Due to their ease of use, their [usage and prominence have increased quite significantly](https://trends.google.com/trends/explore?date=all&q=static%20site%20generator ).

![Static site generator as a search term's usage from 2004 until today](https://imgur.com/uGvDPSS.png)

## Publii

Publii’s [About page](https://getpublii.com/about/) describes it as a “fresh new app on the block that opens up fresh avenues for creating interesting, attractive static websites,” and briefly [discusses](https://getpublii.com/about/) how its two creators have “many years of accumulated academic and practical knowledge.”

Publii has been around since 2016, so it is mature with a large ecosystem around the product.

Some of its [key benefits](https://getpublii.com/) are summarized below:

- It’s safe. The app is “near-impenetrable” to hackers as it works locally, so you don’t need to worry about security updates and manually managing databases to store your work.
- It’s portable. Publii is just a desktop app so you can manage your website anywhere, and it allows multiple users to all collaborate on one website.
- It’s easy to migrate. If you’re moving from WordPress, it has a built-in WordPress importer to transfer your posts, pages and categories.
- It’s fast. The speed of Publii’s web pages is very impressive and they are designed with performance in mind.

We’ll dive into further details of some of these features later, and answer key questions to help you consider which SSG best suits your use case. We’ll cover:

- [Set Up](#set-up)
- [My Publii site](#my-publii-site)
    - [First impressions](#first-impressions)
    - [UI](#ui)
    - [Creating posts](#creating-posts)
    - [Speed profile](#speed-profile)
    - [Search Engine Optimization (SEO)](#search-engine-optimization-seo)
- [Deployment](#deployment)
- [Support](#support)
- [Security](#security)
- [Limitations](#limitations)

### Set Up

It’s really quick to get up and running with Publii. To start, simply go to [Publii’s download page](https://getpublii.com/download/) and download the desktop app.

There are options for MacOS, Windows and Linux depending on which operating system you use, but there are some minimum system requirements that you can find [here](https://getpublii.com/download/).

### My Publii Site

To actually get a feel for using Publii [I made a really simple website](https://kealanparr.github.io/publii-test/), tweaked the UI a little, made some posts with filler text, profiled my site and deployed it out.

#### First Impressions

On first opening Publii I found it really intuitive. It has a really clear left-hand side (LHS) menu with all the options you may want to use (like adding authors, tagging your posts, creating new posts, or changing your UI, etc.)

I was able to quickly produce a basic site and view my changes with a **Preview your changes** button.

I filled out a few posts with some basic template text and looked at the different themes.

Each section was clearly laid out and had lots of sensible defaults prefilled so you don’t have to spend a long time configuring it to make full use of its features.

You are able to create multiple sites which is a great benefit, and I was surprised how much you could do completely offline.

#### UI

Making UI changes with Publii was seamless and easy. Your site is split out into lots of separate sections, so you just find the setting on Publii and change what you need. The **Preview your changes** button lets you really quickly iterate to achieve your desired design.

#### Creating Posts

My website was going to be a really simple blog. Publii offers three different options for generating posts: [WYSIWYG editor](https://getpublii.com/docs/post-editor.html), [Block editor](https://getpublii.com/docs/the-block-editor.html), or a [Markdown editor](https://getpublii.com/docs/the-markdown-editor.html). Having the three options gave me a flexible and convenient way to produce content that best suited me.

Developers tend to use Markdown, which is a way to add formatting elements to your text (like bold, italics, images, and headers).

If you aren't familiar with Markdown, try the What You See Is What You Get (WYSIWYG) editor as it’s similar to traditional word processing with tools to control the whole flow of your content.

#### Speed Profile

Speed is a key concern for websites. If your website takes between one second to three seconds to load, the probability of users bouncing off your page [increases by thirty-two percent](https://www.thinkwithgoogle.com/marketing-strategies/app-and-mobile/mobile-page-speed-new-industry-benchmarks/); that bounce rate increases to ninety percent if a page takes more than three seconds.

So when I finished my website I used Google's Lighthouse to profile the site’s speed.

![Google Chrome Lighthouse Speed Performance](https://imgur.com/usV5rG4.jpg)

It received a perfect score. Very impressive!

#### Search Engine Optimization (SEO)

SEO relates to things you can change on your website to try and optimize how discoverable you are to search engines like Google. I wanted to test Publii’s default SEO settings, so I made no changes before running a Lighthouse test:

![Google Chrome Lighthouse SEO performance](https://imgur.com/nSrYpB9.jpg)

It received a score of ninety out of a hundred, which is impressive, and I think I could have made it higher with some simple tweaks to the default settings.

### Deployment

If you’re not familiar with developer technologies, the deployment process might be tricky. Everything up to this point has been **very** easy to do, and the deployment might be the hardest part, but it is by no means overly difficult.

You’ll have to choose which server you want to use, create any accounts you need depending on the platform, and follow the tutorial.

It took me around ten minutes, and the tutorial was really clear. I went with GitHub pages as I already have a GitHub account. The actual deployment took less than thirty seconds and then, after it was connected, whenever I previewed my changes I could simply “Sync” my current Publii changes to the server to get changes deployed out.

It’s well within the scope of a non-technical person, and I haven’t seen another SSG do this any better than Publii.

### Support

An important part of creating anything is help if you ever get stuck. Publii has quite a few ways to help. Firstly, scattered throughout the relevant places are tutorials of how to do each new thing (like deploying out to servers).

If you can’t find it in the tutorial, or you can’t find the solution in their [documentation](https://getpublii.com/docs/), they also have a [help Forum](https://forum.getpublii.com/) where you can ask any question you can’t find the answer to. 

### Security

Publii’s security is great. Many hacking attempts try to leverage code injection—this allows hackers to run malicious code on your website, but only if there is code currently running.

In static websites, you only send generated website files making the site [“nigh impossible”](https://getpublii.com/blog/publii-static-website-cms.html) to hack without gaining direct access to the server.

### Limitations

The biggest limitation if you choose Publii is that it is a **static site** generator.

If you need a complex, dynamic website that lets users log in and purchase things, and on which you can change stock levels, Publii probably would not be your best choice. Publii isn’t trying to do too much and they have their use cases well laid out.

Another potential weakness I noticed, from reading posts in the official Publii [Forum](https://forum.getpublii.com/topic/is-it-possible-to-insert-a-tag-url-as-a-base-url-for-posts/), was that many users who wanted to configure their post URL's a certain way could not because Publii doesn’t allow that. This use case won't affect my example site, but it may be something to consider.

## Conclusion

I was really impressed with Publii. It is [open source](https://github.com/GetPublii/Publii), fast, and simple to use. The company has shared what’s on the roadmap for the coming years and you can learn more [here](https://getpublii.com/roadmap/), or review what has recently been added. You can quickly look at the effect of tweaking parts of your site, develop it offline, and go from idea to viewing a complete website incredibly fast. Publii listens to its users and it continues to improve with every new release.

I hope this review has been helpful.
