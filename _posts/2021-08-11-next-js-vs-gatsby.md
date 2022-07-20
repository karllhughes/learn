---
layout: post
title: Next.js vs. Gatsby
description: Ultimate comparison guide between Next.js and Gatsby. Which one is to choose?
categories: platforms
cta: Content Ideas
author: shaundai
date: 2021-08-11T13:52:49.538Z
img: /assets/posts/next-vs-gatsby.jpg
---
React frameworks are [software platforms](https://draft.dev/learn/platforms/) that extend the capabilities of React web applications. Certain functionality needed in most blogs and websites (page routing and image optimization for example) don’t come packaged as part of the Create React app; they require libraries and complicated configuration to implement.

Next and Gatsby frameworks include this functionality as defaults, enabling React developers to easily build full sites without much upfront configuration. Additionally, since their individual parts were optimized to work together (vs. installing libraries that came from different places), you begin with an incredibly performant site.

When deciding between a Next or Gatsby framework, how do you determine which one is best? Let’s explore the key differences between the two. We’ll end with some questions to ask yourself to make the best choice.

## Getting Started

Let’s begin with a look at what it’s like to start up a site and compare Next js vs Gatsby.

### What is Gatsby js?

Gatsby is a free open-source static site generator that allows developers to build super fast websites and apps. Their site has extensive documentation, regular webinars and a large community of contributors that allows developers to connect and further their knowledge. 

In addition to comprehensive documentation, Gatsby’s website includes a mini-tutorial that shows new users that building and deploying a Gatsby blog or site takes just a few simple steps. Developers can start a basic site using the Gatsby CLI or choose a pre-styled template from Gatsby’s [library of starter sites](https://www.gatsbyjs.com/starters/?v=2). Starter templates allow users to quickly spin up a beautiful and functional blog without having to fuss about design. Developers can also [create their own Gatsby starters](https://draft.dev/learn/creating-gatsby-starters).

Though getting started is easy, customization can involve a bit of a learning curve. Gatsby relies heavily on [GraphQL](https://graphql.org/) for page routing, fetching API information, and use of plugins (we’ll talk more about this later). If you’ve never worked with GraphQL before, it is worth it to take a quick tutorial to learn the fundamentals.

[Why use Gatsby js?](https://www.gatsbyjs.com/why-gatsby/)

### What is Next js?

Similar to Gatsby, Next.js is a framework that gives the user the building blocks to build a website or app. It is open-source and gives you the tools to create and deploy new applications in a short time frame. 

Getting started with a Next app is as simple as typing in a command in your terminal. Next’s CLI tool create-next-app works the same way as create-react-app, allowing you to spin up a full app with added functionality such as image optimization and page routing included as a set of customizable defaults. From there, a fundamental understanding of React is all that is really necessary to build and customize your Next site.

[Next.js website](https://nextjs.org/docs/getting-started) has comprehensive documentation with details about building a Next app using React or TypeScript. They even offer a free “Getting Started” tutorial to help walk new users through the first steps. Examples of how to use Next with dozens of other popular tools, libraries, and languages can also be found on their [GitHub page](https://github.com/vercel/next.js/tree/master/examples).

[Why use Next js?](https://nextjs.org/)

## SEO

React applications built without a framework like Gatsby or Next have notoriously poor SEO. They use client-side rendering (CSR) to render pages; passing HTML, CSS, and a script tag to the browser when it receives a request for a page. That script tag contains the instructions your browser needs to build all of the React content on your site. To properly index your site for search engines to find, web crawlers need to be able to read that content before your site is run. However, most web crawlers don’t run that browser script as they crawl, so they don’t get all the information about what’s on your page in time to index it.

Gatsby and Next solve this through the way that they handle page rendering. Both provide web crawlers with the full contents of your site before the page is run in the browser, making your site appear in Google search results.

Let’s talk about how both Next and Gatsby framework’s helps with SEO:

### Gatsby

Gatsby uses static site generation (SSG) to pre-render pages. Before deploying a site built in Gatsby, your code goes through a build process where the full HTML site is prebuilt before it even gets a browser request. When a user visits a page built in Gatsby, Gatsby locates the page’s HTML file in your build folder and rehydrates the page in order to make it into a full React application.

![Daniel Wellington’s e-commerce site built with Gatsby](https://i.imgur.com/HopUXlF.png)

After making any updates to your site, the build process needs to be run again in order for the CDN to have the most recent updates. Thus, Gatsby is better for sites that don’t change much during the day such as landing pages, company sites, and blogs.

### Next

Next.js can be used for static site generation, but it was optimized for pure server-side rendering. Server-side rendering (SSR) has been done for years with languages like PHP and .NET, but Next allows us to leverage SSR using JavaScript with Node.js as the runtime server.

![Ferrari’s website built with Next.js](https://i.imgur.com/rj3vfy4.jpg)

Next’s primary differentiator is its use of dynamic rendering (a fancy way of saying “the page is built when the browser requests it”). All of the information for your site (routes, page data, etc.) exists on a Node.js server. When you navigate to a Next.js page from your browser, the server goes to find the page you requested. It is at this time that the page is built, and the data is then sent to the browser for the user to see. For this reason, dynamic rendering is great for sites updated multiple times a day such as e-commerce stores and online forums.

## Fetching and Handling Data

The biggest difference in the methods used to fetch your data will depend on whether your app is statically-generated or server-side rendered. Since statically-generated sites pre-build pages before they are rendered in the browser, they fetch any data they need at build time. By contrast, server-side generated sites fetch the data needed at run time.

<!-- signup -->

### Gatsby

Gatsby does not care which API your data comes from, but it will take and source whatever data it gets back and make it available to you as a GraphQL API. In order to access your data, however, you will need to write GraphQL queries in your code.

GraphQL is great in that it allows for fetching very specific data - like the names of all blog posts with a specific tag, for example. This is meant to improve performance by decreasing network usage. However if you are building a SSG Gatsby blog, all data is fetched at build time and there will be no impact on performance at runtime.

### Next

Next is flexible when it comes to fetching data, leaving it up to users to decide the approach they would like to use. The only piece required when it comes to data fetching is the use of one of their lifecycle methods (getServerSideProps to enable SSR or getStaticProps for SSG) to get the initial props needed to pre-render the page data.

If you plan on fetching large amounts of data, SSR is the better option. Massive amounts of data can cause slow builds in SSG apps. Servers used in SSR, however, are much more powerful and capable of quickly and repeatedly performing these complex operations.

## Plugins, Extensions, and Ecosystems

One reason why Gatsby and Next are so popular is that both easily integrate with other tools and languages you’re already familiar with. Through their partner ecosystems, Next and Gatsby frameworks allow you to further extend the capabilities of your apps without unexpected side effects.

### Gatsby

Unless you’re using a starter, most additional features are not included in your Gatsby file. However, Gatsby is very much like Wordpress in that it has an enormous ecosystem of plugins that allow you to easily enhance your Gatsby app with any functionality you would like to add. Compressing images, adding in the TypeScript compiler, and using a pre-built theme are all examples of capabilities available in Gatsby’s [plugin library](https://www.gatsbyjs.com/plugins).

![screenshot of Gatsby plugin library main page](https://i.imgur.com/r1nWmNi.png)

Through the plugin library, Gatsby has the largest partner ecosystem of any framework. Plugins are available for most tools and libraries you’re already working with, making integrating Gatsby with other tools very simple. If you want custom functionality or themes, you can also build a custom theme or plugin and host it in the plugin library.

### Next

Functionality that has traditionally been difficult and time-consuming to add to React manually— like page routing, image optimization, and code splitting—come as out-of-box defaults that can be easily customized in your Next.js config file.

Next was created by Vercel, a popular deployment and collaboration platform. As a result, Next benefits from Vercel’s incredible ecosystem of partner tools. Next is, of course, optimized to work with Vercel but also works well with other tools and libraries you already use for hosting, styling, and building, making it easy to incorporate it into your tech stack.

## Scaling - Next js vs Gatsby

Will you be the only person who touches your app, or will there be others who maintain it? Are you expecting loads of activity from daily users? The choice between Gatsby vs Next will depend on how large you expect to grow your app in the future.

### Gatsby

Gatsby is best for personal blogs and smaller static sites. When apps become too large, they may become extremely slow during builds or may not build at all. On their [scaling issues documentation page](https://www.gatsbyjs.com/docs/scaling-issues/), Gatsby notes that “large” is typically defined by an app with over 100K pages or with large amounts of data being fetched from the GraphQL API.

### Next

Next is lightweight and easy enough to be used by hobbyists to set up a Next js blog, but also powerful enough to scale for enterprise use. Large organizations with tens of thousands of daily website visitors including Netflix, Hulu, and Nike are running on Next apps hosted on Vercel. When building a large enterprise-scale application, you should reach for Next.js.

![Jet’s eCommerce site built with Next.js](https://i.imgur.com/Zw0TiX1.jpg)

## Hosting - Gatsby vs Next

Now that you’ve built your app, it’s time to host it somewhere for people to use and interact with. Let’s talk about where Next.js and Gatsby apps can be hosted:

### Gatsby

During the build process, Gatsby generates static assets that can be used in the browser and hosted anywhere. You have the flexibility to decide which hosting platform is best for you: Netlify, Firebase, Azure, AWS, Vercel, or whatever your heart desires.

### Next

Similar to Gatsby, Next’s SSG option generates static assets that can be hosted anywhere. However if you choose the SSR route, you have to find a Node.js server to host it. Vercel—the creator of Next.js—is of course optimized to do this. SSR is supported by most of your favorite hosting platforms as well (Firebase, Netlify, AWS), but make sure to use tutorials specific to SSR hosting when you are first learning.

## Gatsby vs Next - Choosing Between the Two

Deciding between these two frameworks comes down to the following questions:

**How often do my pages need to be updated?**\
With dynamic routing, Next is optimized for apps with pages that need to be updated often, such as stores or apps listening for messages. By contrast, static sites need to be rebuilt every time they are updated. If you are creating a blog or site with pages that don’t change frequently, you can use Gatsby.

**Am I building a blog or static site?**\
Gatsby has long been known as a great tool for personal blogs and small static sites. As a result, it has an expansive plugin library with themes that will give you features you will need in your blog so that you don’t have to build them from scratch. If you’re building a small site or blog but don’t want to build every feature from scratch, Gatsby is a great option for you.

**Does this app need to scale?**Gatsby apps are known to run into errors and slow builds when they become too large or fetch large amounts of data. If your app will have more than 100K pages or will need to fetch large amounts of data (such as a store containing many products with variants), Next.js is your best option.

## Conclusion

For optimizing large, enterprise-scale apps or sites with lots of updates, reach for Next.js. For small or static sites and blogs, Gatsby is the optimal choice. No matter which you choose, however, you can expect an optimized React app with out-of-the-box features for enhancing performance, integrating with the most popular third-party tools, and boosting SEO.