---
layout: post
title: Refreshing Old [Technical] Blog Posts
description: Want 61.9% more traffic on your blog in just 5 months? Here's how
  refreshing some of my old blog posts led to a huge uptick in SEO.
categories: writing
cta: Playbook
author: karl
date: 2020-11-22
img: /assets/posts/refresh.jpg
---

When I left my role as a [startup CTO to found Draft.dev](https://www.karllhughes.com/posts/cto-writer), I decided I would invest a little time improving [my personal blog](https://www.karllhughes.com/). I’ve been writing sporadically on the site for the past decade, but before 2020, I wasn’t consistent, and the topics varied widely. As I began writing full-time for clients and learning more about SEO, I decided it was time to make some updates to my personal blog as well.

## Why Refresh Old Blog Posts?
One of the easiest ways to improve an existing website is to improve the content that’s already there. Because you don’t have to start from scratch, you’ll spend less time on each piece of content, and if (like me), you didn’t pay much attention to SEO or keywords or length when you wrote the piece initially, you might get a big lift out of the effort.

My blog has been around for a long time, so it has some domain authority, and a few posts rank well in Google. Still, many of the posts that I thought were good had almost zero search traffic, and some of the ones that had good search traffic were not relevant to my audience. I had also published 200-word summaries of articles that I wrote for other websites, and those were getting zero traffic and [likely hurting my standing in search engines](https://www.searchenginejournal.com/what-is-thin-content-how-to-fix-it/270583/).

The goal of refreshing my blog was to increase the amount of traffic I got from search engines and gain more email subscribers to my newsletter each month. In this post, I’ll show you how I am doing this and what the results have been so far.

<!-- signup -->

## The Challenge in Keeping a Technical Blog Up-to-Date

My blog contains a mix of [developer tutorials](https://draft.dev/learn/technical-tutorials), opinion-driven technical thought leadership pieces, and collections of books and [tools I find useful](https://draft.dev/learn/tools/). While most of the posts written in the past couple of years weren’t too bad, many of the older posts are now full of deprecated references and technologies.

Blog posts will suffer in search engines if they get out of date or factually inaccurate. If you write a lot of tutorials, this can make keeping your blog relevant incredibly hard. You might spend half your time just keeping old posts updated.

## Planning My Content Update
In deciding how I would go about the content refresh project, I ran across two compelling case studies that serve as good examples of successful refreshes. These served as inspiration and gave me enough information to plan my content update.

### Case Study 1: [Recovering from a Google Penalty](https://alphainvestors.com/case-study/reviving-a-penalized-site-to-6400-visits-per-month-case-study/)
While many SEO case studies show how to increase your traffic to rank new websites, there aren't as many available where people talk about how they recover penalized websites.

In this article by Servando Silva of Stream SEO, the author walks you through a site he helped recover from a Google penalty. By removing low-quality content, beefing up existing posts, and removing problematic backlinks, Silva increased the nearly dead site to more than 6,000 visits per month.

My blog didn’t have the spam backlinks problem that Silva’s did, but I did have some low-effort content that needed to be removed or improved.

### Case Study 2: [Pkwy Digital’s Keyword Optimization](https://www.pkwydigital.com/case-study-update-old-blog-posts/)
Another area of search engine optimization I had never paid much attention to was keyword optimization. Pkwy Digital’s problem was similar in that they had lots of posts that ranked in the 6-10 spots on Google but very few in the top 5.

Those coveted top 5 spots are where [almost 70% of the clicks land](https://www.amazeemetrics.com/en/blog/the-top-5-results-in-google-get-almost-70-of-all-clicks/), so if you can bump the ranking of a post in the bottom 5, you can make a significant impact on your post’s performance in Google. After making some keyword optimizations and combining similar posts, Pkwy increased their average search engine clickthrough rate from 1.8% to 4.9%.

That means that if they were getting 100,000 monthly search impressions, they would have gone from 1800 monthly visits to 4900. That could be huge for a small site like mine that was getting 1500 pageviews a month from search engines.

## Five Methods for Refreshing Old Blog Posts
Armed with these two case studies and [ahref’s fantastic guide on refreshing blog posts](https://ahrefs.com/blog/double-your-blog-traffic/), I set out to start improving my blog. Here are the five tactics I used in various cases to update my old blog posts:

### 1. Remove Irrelevant Content
Following [ahref’s suggestions here](https://ahrefs.com/blog/content-audit/), I looked through all 200 posts on my blog and found all of them that were receiving little to no traffic. Of those, I removed and redirected any that were off-topic, very short (<500 words), or about old technology that was no longer relevant.

![Irrelevant content from my blog](https://i.imgur.com/GDOqlds.png)

A few posts that got very little search traffic still performed well on social media, so I decided to keep them around for possible updates later. Of the posts I removed, I redirected most to the homepage using [a Cloudflare Worker](https://developers.cloudflare.com/workers/examples/redirect). A few posts that got little traffic were similar to another, so I redirected them to the other article.

By removing this irrelevant content, I’m showing Google that a higher proportion of my content is high-quality. This will lead to an overall increase in site reputation over time as Google registers the changes.

### 2. Merge Redundant or Similar Posts
I had written four blog posts about my process for hiring software engineers. The first mentioned a specific job posting that had long since expired, the second told how I was revising my hiring process, and the third and fourth told the results of these revisions.

While having multiple posts about similar topics isn’t bad, I felt like there wasn’t enough unique content in each post to justify having four of them. Plus, some of the information was out of date and no longer helpful.

So, I took all four posts and merged them into the URL with the most backlinks and search traffic already (which happened to be the oldest one). [This new post](https://www.karllhughes.com/posts/hiring-process) is essentially a complete rewrite, although it uses pieces of each of the original posts. It’s much longer but broken into scannable sections so that readers can easily jump to the parts they need.

### 3. Update Existing Posts That Rank Well
In 2015, I wrote a post about [how I spent my time as an engineering manager](https://www.toptal.com/engineering-management/a-day-in-life-engineering-manager). After tracking my time every day for months, I gave readers detailed insight into a day in the life of an engineering manager.

This post has done pretty well in search engines, ranking for a few terms that are very relevant to my blog’s audience. Unfortunately, even good blog posts tend to degrade over time, so by 2020, much of the luster had faded. I figured I would try to update the post to restore a bit of its former glory.

Here’s what I did to improve posts that already ranked pretty well but needed a refresh:

1. Update technical details and add more relevant sections.
2. Add original media (images/video) and [update the alt tags](https://www.w3schools.com/tags/att_img_alt.asp).
3. Ensure relevant low-competition keywords were present in headings.
4. Improve the introduction and meta description to boost clickthrough rate.

Each post I update is more current, longer, and more likely to jump back up in the search rankings after the refresh.

### 4. Build Internal Links
Another series of posts that performed okay in search engines were all related to software testing. Unfortunately, none of the posts linked to each other. While internal links don’t count for as much as external links do, they [still help ensure Google knows which pieces of content might be related](https://moz.com/learn/seo/internal-link) and they encourage readers to visit more pages.

I looked through all the posts on my site and added categories. Then I looked for opportunities to link relevant posts to each other. I doubt this will dramatically improve my search rankings alone, but it’s not a bad idea.

### 5. Update Post Dates and Re-Promote
Finally, after I updated each post, I updated the published date and put it through my [technical blog post promotion checklist](https://draft.dev/learn/promotion) again. I had promoted these posts once when they were first published, but that was years ago. After refreshing them, the content was different enough that promoting them again seemed like an easy win.

In the case of my post on _A Day in the Life of an Engineering Manager_, sharing it led to an additional 728 visitors to a post that was originally posted five years ago!

## Results of My Content Refresh
As of this writing, I’ve only updated a handful of my blog’s old posts, but I can already tell that the refreshes are having an effect. Here’s an example of the traffic to the _Engineering Manager_ post I mentioned above:

![Effect of a content refresh on a piece of content](https://i.imgur.com/OQm2k83.png)

The orange line is the traffic to the post between October, 12 and October 31st while the blue line shows what happened to traffic after I refreshed the post on November 1st. There were a couple of spikes when I shared it out on social media, but the baseline search traffic also rose.

This chart shows pageviews from Google before and after the refresh:

![Effect of a content refresh on search engine traffic](https://i.imgur.com/4R1H62z.png)

While not much time has passed, it looks like Google is showing more people this article or clickthrough rates have gone up dramatically. I’ll have to dig into Webmaster Tools to be sure.

This increase in search traffic isn’t just limited to one post. Organic search traffic is up 61.9% on the site since I started this refresh effort in June.

![Organic search traffic since refresh started](https://i.imgur.com/2K1kKpp.png)

Six months is not enough time to see the full effect of an update like this that’s still ongoing, but it does seem to suggest that refreshing old blog posts will work. I’ll report back on this as I continue to refresh my blog’s old content over 2021, so hopefully, we’ll have a more complete picture then.

If you'd like any help creating or refreshing content for your blog, [book a call with me](https://draft.dev/call). I'd love to help you out or just walk through the process with you.
