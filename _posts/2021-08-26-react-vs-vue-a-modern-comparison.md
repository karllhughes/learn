---
layout: post
title: "React vs. Vue: A Modern Comparison"
description: "React or Vue: read this article to decide which one to choose"
categories: platforms
cta: Call
author: piero
date: 2021-08-26T06:59:00.035Z
img: /assets/posts/2c835436.jpg
---
Choosing the best frontend framework can be a daunting challenge. New technologies are created every year, especially in the frontend development environment, and you may worry about making the wrong choice. 

In recent years two frameworks have dominated the frontend scenario, enabling thousands of applications to be built and appearing in most tech companies’ job requirements: React and Vue. 

How you select between the two will depend on your needs. The key is in using the proper criteria to make your choice. 

## Criteria

There are many factors to consider in picking a framework. Here are some of the most important:

* Code structure
* Performance
* Scalability
* Learning curve
* Talent research

Let’s go into each factor in more detail.  

### Code Structure

React and Vue are similar in many ways, but there are a few differences to keep in mind. 

React uses JSX, which makes it easier for JavaScript to embed HTML in React. JSX can be daunting for newcomers, but it also helps make React more semantic and more scalable.

Vue uses HTML templates. This is a common concept for a lot of developers, but the templates can pose limitations for enterprise-level applications due to their manageability.

React natively supports components, essential state management, and DOM manipulation tools. Other tools like Redux are separate and must be installed and integrated into your project.

Vue, meanwhile, has a highly active set of core solutions, like Vue Router and Vuex, which are constantly maintained and improved by the team behind the framework.

### Performance

Usually, comparing the performance of two front-end frameworks means looking at three stats: DOM manipulation speed, startup time, and memory allocation. From [this website](https://stefankrause.net/js-frameworks-benchmark8/table.html), you can see how these frameworks compare.

For example:

![DOM manipulation performances in both React and Vue](https://i.imgur.com/iShv6oK.png)

You can see from this first metric that both tools are similar in DOM manipulation. However, React is significantly slower in the swap rows category.

Now look at how the frameworks compare for startup time and memory allocation.

![Startup time performances in React and Vue](https://i.imgur.com/80pv21Z.png)

![Memory allocation performances in React and Vue](https://i.imgur.com/3LMystw.png)

These metrics show Vue is the clear winner, even if React is an excellent competitor.

In general, both frameworks are similar in performance. They both make use of virtual DOM and lazy loading. However, Vue appears to be more lightweight, with a better tracking of dependencies to prevent unnecessary re-renders.

React supports the ability to prevent useless renderings. But it comes at the cost of using built-in lifecycle methods, which are not always easy to use and can lead to performance problems and infinite loops inside the app.

### Scalability

Due to its template-based approach, Vue is not the best for creating large applications, as HTML templates can become nearly impossible to manage. The framework does offer good support for small to medium multi-page applications, which can be slowly integrated into an existing project.

React performs well on any size application. I’ve worked with React enterprise-level apps many times. Thanks to its JavaScript approach, this framework is easy to scale with classic code organization techniques.

### Learning Curve

Both frameworks use HTML, CSS, and JavaScript as their core technologies, but I find Vue significantly easier to grasp than React. React requires the use of JSX, which can be confusing for beginners as they learn a new approach to writing code and managing views.

Vue’s HTML templates are familiar to most developers, and the framework’s documentation is regarded as more detailed and wide-ranging than that of React.

### Talent Research

Maybe you’re trying to pick a framework, not for a project but to base your career skills around. React proves to be the top option. The [Stack Overflow 2021 Developer Survey](https://insights.stackoverflow.com/survey/2021#section-most-popular-technologies-web-frameworks) shows React is the most popular framework choice, beating jQuery and well ahead of Vue. 

![Source: Stack Overflow 2021 Developer Survey](https://i.imgur.com/PyIOfmY.png)

The tech trends site [BuiltWith](https://builtwith.com/) also notes that projects built with React are more than double the projects made with Vue. So React may still be the best career choice.

Some famous apps built with React include: 

* Facebook
* Instagram
* Netflix
* Khan Academy

While famous apps built with Vue include:

* Nintendo
* Behance
* GitLab
* Netlify

### Bonus: Blogging

As a content creator, I’m interested in creating and hosting my own blogging platform. As a developer, I’m interested in how React and Vue would compare for this purpose.

One new development over the past few years is the static site generator (SSG), a software application that creates HTML pages based on raw data and a template. An SSG is an excellent technical choice for building a blog.

Both React and Vue support SSGs, but honorable mentions should go to Gatsby.js and Gridsome.

Gatsby is an open-source framework based on React and ideated to allow the creation of super-fast websites. It offers various tools like code-splitting, image optimization, and an internally generated GraphQL API for your project. It also features a rich collection of plugins for extending its support to other technologies.

Gridsome is similar to Gatsby, but it uses Vue as its core technology. It supports every headless CMS and every API. It also offers amazing support for PWAs, loading only necessary code into your website and allowing navigation to perform at top-tier levels.

For more info about comparing these tools, check out [this article](https://www.tekkiwebsolutions.com/blog/gatsby-vs-gridsome/).

## Conclusion

Clearly, each framework offers pros and cons for developers. Vue may not be the best choice for large applications, but it will be easier to begin using than React’s JSX. React is the most used framework in 2021 and the most desired by companies. Vue offers a more lightweight solution for your projects and can be more easily integrated into an existing project. Both frameworks, though, work with many other tools and can help you power your SSG page. 

How you weigh this information depends on what your career goals are and what you need to accomplish with a current or future project. Keep your priorities in mind and you’ll be able to make the right choice for your needs.  

