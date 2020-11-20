---
layout: post
title: How to Write a Technical Tutorial
author: josh
date: 2020-11-15
description: "We write hundreds of technical tutorials every year, so in this post, we've collected some of our top tips for writing great software development tutorials."
categories: posts
img: /assets/posts/technical-tutorial.png
---

Technical tutorials offer compact lessons on various technical subjects from general programming to web development to large scale infrastructure and beyond. They are usually short enough to be digested in one sitting (1500 to 3000 words) and aim to solve a specific problem using a particular technology or set of technologies.

We write a lot of tutorials for software engineers at [Draft.dev](https://draft.dev), so in this guide, I’ll share a little bit of why and how we write technical tutorials.

<!-- signup -->

## Why Write Technical Tutorials?
There are several reasons people decide to write technical tutorials. Here are a few of the most common ones:

### 1. SEO (Search Engine Optimization)
Technical tutorials are a great way to draw traffic to your site. Most engineers spend their day Googling for answers to difficult problems. If you’ve ever worked as a software engineer, you know it can be especially hard to find tutorials that use newer technologies or novel combinations of technology.

If you know the types of things your customers are searching for, you can cater to your content accordingly. For example, a company that offers payment processing services could publish a tutorial about accepting payments in a Node.js app. A hosting company could write about using their platform to deploy a Python workload.

The goal here is to write tutorials that answer common questions so that engineers will find them when they search for the topic on Google.

### 2. Solidify Your Learning
[Studies have shown](https://onlinelibrary.wiley.com/doi/abs/10.1002/acp.3410?campaign=wolearlyview) that teaching a subject can enhance your understanding of the material.

Writing technical tutorials is a great way to boost your learning. Many people think that they can’t write technical articles because they are not an “expert” in the subject matter, but **some of the best tutorials are written by writers who are just learning the material themselves**.

Writers who are new to a subject are closer to a _learner’s mindset_, which allows them to anticipate the types of questions a reader might have and fill in gaps they wish were clearer when they first learned the material.

Explaining a complicated topic to others forces you to slow down and question your assumptions. In the end, you will retain the information more completely if you teach others about it.

### 3. Showcase Your Skills
Like pushing your own projects to GitHub or making pull requests on open-source projects, writing technical tutorials is a great way to showcase your talents to potential employers. Writing gives you the chance to show off some of your code, talk about your decision-making process, and highlight your problem-solving skills.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">If you want to stand out as an engineer, build small things and write about them. ✍️<br><br>It&#39;s easy to start a big project and never finish it. Instead, bite off something you can do in a weekend and then write a blog post about it.</p>&mdash; Karl L Hughes (@KarlLHughes) <a href="https://twitter.com/KarlLHughes/status/1306221716356706305?ref_src=twsrc%5Etfw">September 16, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

### 4. Help People Use Your Product
Building a great software product is hard. Convincing users to use your new product can be even harder.

Having great documentation is important, but you can further entice new users with technical tutorials that showcase your service in real-world projects. This adds context for potential customers who may be new to a particular technology or are unsure if your product is right for their project.

## Tips for Writing Great Technical Tutorials
Just because you know a topic well doesn’t mean you’ll crank out a great tutorial on the subject. Here are a few things to keep in mind to help you write informative, engaging, and useful technical tutorials:

### 1. Know Your Audience
Understanding your reader is crucial to writing a technical tutorial.

Writing is about making choices regarding what to include and what to leave out. You have to decide if you’re going to spend two paragraphs explaining something or simply provide a link to an outside source. You won’t be able to make any of these decisions if you don’t know **who you are writing for**.

This tutorial on using [Amazon S3 to serve static files in a Django app](https://www.caktusgroup.com/blog/2014/11/10/Using-Amazon-S3-to-store-your-Django-sites-static-and-media-files/) assumes the reader already knows how to use Django and Python.

![An example of a technical tutorial](https://i.imgur.com/2PnnvcY.png)

Because of this, it doesn't go into great detail about setting up a Django app, but it does take great care in laying out the concepts around Amazon S3 and how they integrate with Django in particular. We could say the audience for this article is “experienced Python developers who are relatively new to Amazon S3.”

Before you start your next tutorial, try writing a sentence or two about who your audience is. It will help you stay focused as you write.

### 2. Provide Context
Don’t tell your reader **how** without first answering **why**.

This is where most technical articles fail. They meticulously document steps - *download this package, write this code, add this config file, etc.* - without ever explaining the purpose of these steps or how they might change under different circumstances.

Steps are how Ikea instructions are written. **No one has ever assembled a shelf from Ikea and then turned around and claimed they could build their own from scratch.** Sure, I see they used this type of screw, but why? I want my bookshelf to be half as wide and twice as tall. Will it still be stable?

This article about [Postgres Views in Ruby on Rails](https://pganalyze.com/blog/materialized-views-ruby-rails) uses a real-world dataset of hockey teams and top scores for its examples.

![An example of a technical tutorial with context](https://i.imgur.com/b1fHQat.png)

The writer does a great job adding context to each step, which strengthens the reader's understanding of the concepts. After finishing the article, the reader doesn’t just know how to build a hockey data view. They leave with an understanding that will allow them to use Postgres views in Ruby on Rails any way they want.

### 3. Have a Clear Introduction and Conclusion
Readers of technical articles are looking to solve problems and learn new skills quickly. Your introduction should be concise, and it should answer these three questions right away:

1. What will the reader learn?
2. What skills will the reader need?
3. What problem does this technology help solve?

This article about [building an SMS reminder tool for teachers](https://www.nexmo.com/blog/2020/06/04/build-an-sms-reminder-tool-for-teachers-using-google-classroom-dr) explains the problem it’s trying to solve and how it’s going to solve it immediately in the first two paragraphs.

![An example of a technical tutorial with a strong introduction](https://i.imgur.com/3IPpy1R.png)

Your conclusion should mirror your introduction and answer the following questions:

1. What did the reader just learn?
2. What problem was solved?
3. What next steps can the reader take if they want to learn more?

### 4. Provide Code Snippets
It’s always helpful to provide unique code, dependencies, and configuration files that are required for your technical tutorial. You can provide a link to your completed project on GitHub if you want, but you’ll need to be selective about what code you include in the article itself.

A few things to keep in mind as you include code samples:

- ***Break them down into digestible chunks***. Don't provide 80 lines of code and then tell your reader to copy and paste it. Better to choose smaller sections of code that are more digestible, making sure to explain what each line does.
- **Format your code correctly**. Code that isn't formatted correctly is difficult to read and, therefore, difficult to understand. Find a [style guide](https://draft.dev/learn/posts/styleguide) for the language you're working in and make sure your code sticks to the standards agreed upon by the community.
- **Don't forget about file structure**. This usually only applies to large projects, especially when working with React or Ruby on Rails. In these frameworks, the location of your files can affect how and if it runs. It's sometimes helpful to provide the file name and path at the top of the code snippet in the form of a comment:

```Python
# blog/models.py

class Post:
  # ...
```

### 5. Promote Your Work
A technical tutorial needs an audience.

Sharing your work with others is a great way to find more writing opportunities, so don’t be afraid to promote your tutorials on social media or start an email newsletter. Ask your readers for feedback on what worked and what could have been clearer in your tutorial. Taking feedback is essential to improving your writing skills.

If you need help with promoting your tutorials, check out our [content promotion checklist for technical blog posts](https://draft.dev/learn/posts/promotion).

## Conclusion
In this article, I broke down some of the reasons you might want to write a technical tutorial. Whether you're interested in growing your business, advancing your career, or leveling up your skills, writing technical tutorials can offer many advantages.

Finally, I broke down some of the crucial components of useful and informative technical tutorials. If you need help writing technical tutorials or you’d like to work with our team of writers to build content that reaches software engineers, [contact us today](https://draft.dev/#call).

