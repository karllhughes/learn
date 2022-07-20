---
layout: post
title: Hugo vs. Gatsby
description: In this article you will learn advantages and disadvantages of two
  JAMStack static sites, Hugo and Gatsby.
categories: platforms
cta: Content Ideas
author: matias
date: 2021-06-16T23:58:09.138Z
img: /assets/posts/c4f82d27.png
---
JAMStack, which stands for JavaScript, API, and Markup, is the latest buzzword in the world of web development. It aims to drop the complexity of your system, and helps you to deliver better apps in less time. As with any new innovation in tech, there is a plethora of companies offering competing JAMStack options. How can you choose which is the right one for you?

There are two main types of JAMStack sites: static, in which assets are created at build time ahead of deployment, and directly served when the user creates the website; and dynamic, in which a server creates the content and assets every time a user lands on your site.

In this article, we’ll be focusing on static sites and comparing the two most popular solutions: [Hugo](https://gohugo.io/) and [Gatsby](https://www.gatsbyjs.com/). You’ll learn the advantages and disadvantages of each, and which one would be best for your specific use case.

<!-- signup -->

## Why Static Sites?

You may be wondering why we have chosen to focus on static sites, rather than dynamic. The static architecture delivers lightning-fast websites and, more than anything, less complex systems with a decoupled frontend where you can consume data from any data source.

## What Is Gatsby?

To answer, ‘What is Gatsby’ in simple terms, we can refer to how Gatsby describes themselves, and that is as,  a static site generator  or “React-based open-source framework for creating websites and apps.” It has a complete build system that enables you to use web technology to create static files. You will write React code to make your site and consume data through a GraphQL layer. Gatsby will then build your site to create multiple static files that you can deploy.

More on ‘[What is Gatsby?](https://www.gatsbyjs.com/)’

## What Is Hugo?

Hugo (also known as Hugo js) describes itself as “the world’s fastest framework for building websites.” Hugo (SSG) is a static site generator written in Go with the idea of high performance in the build process. Hugo has its template language based on HTML that enables you to create your site. It also supports Markdown and other languages through plugins.

More on ‘[What is Hugo?](https://gohugo.io/about/what-is-hugo/)’

## What Are the Key Differences?

When comparing the two tools, these are the key aspects you want to focus on:

* Learning curve
* Documentation
* Speed
* Security
* Flexibility
* Scaling
* Price
* Community

### Learning Curve

![Hugo Layout Example](https://i.imgur.com/uG6ibIo.png)
![Gatsby Layout Example](https://i.imgur.com/qciziRE.png)For a developer, the learning curve is an important aspect to consider when selecting a tool; this will help you define how much time you will need to deliver value to your user.

Gatsby is built on top of React as the “templating” language, so if you know React and JavaScript in general, you are all set to start working with Gatsby. The next step in this curve is to understand how to work with [graphql](https://graphql.org/). Gatsby uses a graphql layer to collect the different data sources from [various plugins](https://www.gatsbyjs.com/plugins) to be consumed by your React code. However, Gatsby does provide many templates or ready-to-use “[starters](https://draft.dev/learn/creating-gatsby-starters)” that can help you avoid the complexity of React and graphql. Most of this can be found in the [Gatsby docs](https://www.gatsbyjs.com/docs/) resource on their website.

On the other hand, Hugo is built with Go, but you don’t necessarily need to know Go to use it. If you choose to use a pre-made template, then your work will be mostly related to TOML files for configuration and Markdown for the content files. Still, if you want to customize your site or build from the ground up, you need to know how to write your templates using [Go’s templating system](https://golang.org/pkg/text/template/).

So the learning curve depends on your goal:

* Do you want to customize your site from the ground up? Then if you’re familiar with React, Gatsby will be a quick choice
* Do you want to get up and running with ease? Hugo js is a solid choice due to its hundreds of quick-start themes.

### Documentation

![Gatsby Documentation](https://i.imgur.com/nVvtiJn.png)
![Hugo Docs](https://i.imgur.com/kgDaNmI.png)

Every time you are about to start a project with something new, it is a good idea to take a look at the state of the documentation of the chosen technology. As you’ll often have to refer to the official documentation to answer queries, you’ll want it to be easy to use and up to date.

Both the Hugo and Gatsby framework have good documentation that quickly drives you to their corresponding Quick Start guides to help you start.

Gatsby’s documentation is extensive. It has a full-featured tutorial and in-depth guide that runs you through all the nuances of the framework. A simple view of Gatsby’s documentation seems complete but also can be overwhelming.

Hugo’s documentation can be seen as a smaller collection of guides but still with a lot of in-depth information about the framework’s operation. More information can be found at the [hugo docs](https://gohugo.io/documentation/) page.

So, when looking at both Hugo and Gatsby docs,, there’s no clear winner, and it will simply depend on your familiarity with the technology.

### Speed

One of the selling points of a JAMStack site is speed, but you need to split this concept into at least two different metrics. Build speed and Runtime Speed.

Gatsby says that the framework is “fast in every way that matters,” while Hugo preaches that they are the fastest tool out there.

#### Build Time Speed

Since we are talking from a developer perspective and both of these tools leverage the power of the build system to create static sites, the build time speed is a good metric that can be part of your decision.

In this race, Hugo is a clear winner without a doubt. Hugo was built to deliver “blistering speed,” and only takes around 1ms per page. And one of the biggest benefits of Hugo SSG is the lightning fast build time. Gatsby, on the other hand, takes a considerable amount of time in comparison.

Build time speed will depend on the number of pages to generate and the latency of the data sources. An excellent way to compare this speed is just by having the same amount of markdown files as a source for both frameworks, with Hugo SSG coming out on top every time.

Gatsby does offer incremental builds inside their cloud service that aim to provide better build times, but at the same time can lead to vendor lock-in.

#### Runtime Speed

Analyzing the runtime speed can be tricky and will depend on more variables than just the framework. But simply: Gatsby creates HTML pages from your React code to serve the essential app shell and then injects some JavaScript (including React library and any other 3rd party library) to continue the rendering process. This can be seen as slow since there is a JS bundle to load, but at the same time can be an advantage since through this process Gatsby offers other optimizations out-of-the-box such as: Progressive and responsive image loading, and inline critical CSS.

Hugo creates the static HTML pages from the Go templates and includes optional JS compiled with esbuild.

Here the comparison is challenging since simple load HTML and other static assets are fast for both solutions. Still, in some cases, the progressive enhancements offered by Gatsby can be useful or essential to a site, which gives it a slight edge.

### Security

Both offer security as one of their selling points; Gatsby advertises that since they generate static HTML at build time, there is no server, avoiding malicious requests, DDOS attacks, or data exposures. But, the same is essentially true of the  Gatsby static site generator or any other SSG.

You could argue that since Gatsby heavily utilizes JavaScript, then a security issue could arise based on the number of unknown and uncontrolled npm packages involved.

Hugo has a [documentation section](https://gohugo.io/about/security-model/) to talk about the security model they offer. General Data Protection Regulation (GDPR) is an EU law on data protection and privacy, and [Hugo docs](https://gohugo.io/documentation/)  describe in detail how to configure your site to meet the regulations.

But in general words, an SSG holds its weight in terms of security from holes that can arise from 3rd party issues. As an example, [this is a comment](https://github.com/postcss/postcss/commit/8682b1e4e328432ba692bed52326e84439cec9e4#commitcomment-49713297) from a vulnerability issue found in postcss, which states:

> The issue is not critical (it can affect only online tools like CodePen…)

So in terms of security, you can consider that both the Hugo and Gatsby frameworks have similar or even equal security features.

### Flexibility

What is the level of customizability that each framework offers? Do Gatsby and Hugo let you create what you want, or are there limitations on design?

Here, both frameworks offer full features on customization; Gatsby’s framework allows you to create any component you wish with React and any UI library or CSS solution you prefer: tailwind, emotion, or just plain old CSS. Hugo is also free of design opinions, so you are free to implement any UI you wish with the tools available: Go templates and any CSS framework.

Both solutions are equally flexible, so it just depends again on what framework you are more familiar with: React for Gatsby, or Go for Hugo.

### Scalability

Scalability is the ability of the framework to handle large and growing sites. Both solutions have their own take on how to confront the challenge.

Gatsby is known for a slow-building process that creates many different pages, so it can be tedious to work with big sites. They even have an [entry in the documentation](https://www.gatsbyjs.com/docs/scaling-issues/) to address this topic in particular.

They mention that they have acknowledged that Gatsby has scaling issues when the application [has more than 100K pages](https://www.gatsbyjs.com/docs/scaling-issues/#when-can-a-scaling-issue-arise) or when the graphql queries are too large. There’s even a [GitHub issue about scalability](https://github.com/gatsbyjs/gatsby/issues/19512) where the engineering team recollects benchmark data.

One way they offer to solve this building scalability is with their cloud system, but this is an imperfect solution.

On the other hand, Hugo prides itself to be blazing fast for building thousands of pages, so we can say (again) that Hugo here is a winner if we’re looking purely at scalability of build.

But static sites are built, or updated, way less often than they are read, so the other important point on scalability is how well they behave under heavy load.

The JAMStack is, by default, almost infinitely scalable. Since SSG pre-render the assets, the Time to First Byte (TTFB) is minimal. Also, the files can be served through a CDN and be available almost instantly for the user (and use the great HTTP caching capabilities to make it even faster), therefore lowering the server requirements. Hugo and Gatsby fall into this category of frameworks, so their scalability features are on par. Still, if you consider the built time an essential metric for your scalability needs, then Hugo has the advantage.

### Price

Another essential aspect to consider when reviewing tools for your marketing site (or any site for that matter) is price.

Both Gatsy and Hugo are free and open-source. You can download them and use them for free, and the only cost you’ll have to worry about is deployment.

To deploy a site built with Hugo or Gatsby, check some CDN services like AWS, Netlify, or Vercel. Most of these services have a free tier to enable you to start as fast as possible. The other possible cost is related to your data store or CMS, which depends on the service you are using.

So as both frameworks are free, this one is a tie.

### Community

![Hugo Community Discourse](https://i.imgur.com/nxK7FE4.png)

![Gatsby Community Resource](https://i.imgur.com/Ev4ZTuf.png)

With every tool or technology, having an active community can be a huge bonus, particularly if you run into an issue that’s not covered by documentation. In this case, the Gatsby framework is a clear winner, with a thriving and growing community complete with global events and conferences.

## Conclusion

![Hugo vs Gatsby](https://imgur.com/j9ScdkO.png)

Both Gatsy and Hugo do a great job in every category that matters for comparison, with Gatsby drawing an ever-so-slight edge in the community aspect. But, I think it all boils down to your development team’s experience: if your team is already experienced with javascript and React, then Gatsby is an excellent choice to start right away, and if JavaScript is not a tool you have under your belt, then the learning curve of Hugo js  will be lower, so it can be a great alternative.