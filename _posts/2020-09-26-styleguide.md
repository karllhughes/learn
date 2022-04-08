---
layout: post
title: The Draft.dev Technical Blogging Style Guide
description: A style guide includes expectations for your contributors. In this
  post, we break down our technical blogging style guide at Draft.dev.
categories: processes
cta: Call
author: karl
date: 2020-09-26
img: /assets/posts/style-guide.jpg
---
As your blog grows and you [get more writers to contribute](https://draft.dev/learn/finding-motivating-writers), you need to build documents and processes to help you maintain high quality and consistent style. To serve this goal, you should create a style guide to help writers and editors stay on the same page.

Generally, **a style guide includes expectations for your contributors**. Depending on your priorities, you may include more or less information than we do at [Draft.dev](https://draft.dev), but our style guide should give you an excellent place to start. We send this style guide to all new contributors to ensure they are familiar with our expectations, and we refer to this guide throughout the [editing process](https://draft.dev/learn/5-steps-to-a-quality-edit-for-your-technical-blog).

Of course, ours is not the only example of a technical writing style guide. If you're looking to compare your options, check out [Google's developer documentation style guide](https://developers.google.com/style), [DigitalOcean's technical writing guidelines](https://www.digitalocean.com/community/tutorials/digitalocean-s-technical-writing-guidelines), and some of the [other guides here](/learn/technical-writer-style-guides). If you're creating a style guide, I'd recommend reading over several and deciding what you want to include in yours.

## The Draft.dev Technical Blogging Style Guide

At [Draft.dev](https://draft.dev), we specialize in creating technical blog content for companies that want to reach software engineers. While most of our writers are software engineers first and authors second, we still expect them to follow consistent standards for each of our clients.

Below is our style guide, which is broken up into four sections:

1. [Voice](#voice)
2. [Content](#content)
3. [Conventions](#conventions) 
4. [Communication](#communication) 

### Voice

#### Write in Second Person

Speak to your readers directly using "you" and "your." Avoid "we" and "our."

Good:

> You can use a web browser (like Chrome, Safari, or Edge) to access web sites on the internet.

Bad:

> We can use our web browsers (like Chrome, Safari, or Edge) to access web sites on the internet.

#### Use Conversational, Business-Appropriate Language

Read your article out loud and ask yourself, "Would I talk like this at work?" Use your real-world experience, but avoid jargon when possible.

Good:

> Experts agree that the internet was not the product of any individual mind, but a series of advances in networking and computer science.

Bad:

> Many scholars would agree that, had it not been for active networks, the simulation of Lamport clocks might never have occurred. The notion that end-users synchronize with the investigation of Markov models is rarely outdated. A theoretical grand challenge in theory is the important unification of virtual machines and real-time theory. To what extent can web browsers be constructed to achieve this purpose?

#### Don't Repeat Yourself

Eliminate wordiness. You shouldn't repeat yourself when programming, and you shouldn't repeat yourself when writing.

Good:

> A lively debate rages among software developers. The contentious issue is: tabs or spaces?

Bad:

> There is currently a lively, ongoing controversy among many computer scientists and other professional in the field of software development: theories are being spun and arguments are being conducted among them about whether the use of tabs to designate indentation in a document is superior to the use of spaces for the same purpose.

### Content

#### The Introduction

Every article should have a 1-3 paragraph introduction. A good intro needs to answer a few questions right away:

* What's the pain point I'm addressing here? How do I hook my readers? 
* What's the solution to this problem?
* What am I going to do in this article?

Make sure your introduction is completed by letting the user know how you're going to teach them to solve this pain point.

#### Support Claims With Evidence

For every claim you make, ask yourself, "How can I prove this?" You can do this by:

* Including a link to a reputable article
* Including a quote from another source
* Citing an academic study
* Linking to the official documentation
* Interviewing knowledgeable professionals

Good:

> While \[Postgres can handle hundreds of columns](https://nerderati.com/2017/01/03/postgresql-tables-can-have-at-most-1600-columns/), it might not be a good idea to take advantage of this feature.

Bad:

> While I'm guessing Postgres can handle a lot of columns, it might not be a good idea to use more than a hundred if you can help it.

#### Plagiarism and Copyright Infringement

Written content that is copied directly from another source must be quoted and cited appropriately. Switching out a few words in a sentence is not enough to make the content original, so be sure to put everything in your own words.

Bad:

> I've always thought that measuring programming progress by lines of code is akin to measuring aircraft building progress by measuring weight.

Good:

> “Measuring programming progress by lines of code is like measuring aircraft building progress by weight.” - Bill Gates

The bar for using images is even higher. You may not use images from another website unless they expressly allow it. If you need stock images, use a site like [Unsplash](https://unsplash.com/) or [one of the options here](https://draft.dev/learn/free-stock-images).

#### The Conclusion

Every article should include a 1-2 paragraph conclusion. This should restate the thesis of the article and remind readers what they learned. It may also include other resources readers can reference to learn more.

Good:

> While JSON data types come with some drawbacks, they are useful when you need more flexibility in your data structure. Thanks to Django's native support for \`jsonb\`, you can get started using JSON data in your web applications without \[learning all the native Postgres query operators](https://www.postgresql.org/docs/current/functions-json.html).
>
> Next time you need more flexibility in your data model and want to benefit from the strengths of Postgres give \`jsonb\` fields a try.

### Conventions

#### Write in Markdown

All articles should be written in [Markdown](https://guides.github.com/features/mastering-markdown/) and submitted in the [Google Doc](http://docs.google.com/) sent to you when you accept the assignment.

Good:

> Markdown is a formatting language often \*used by static site generators\* and \*blogs\*. If you aren't familiar with its syntax, you can \[click here to learn more](https://guides.github.com/features/mastering-markdown/).

#### Include Unmarked and Annotated Screenshots

If you need to circle something or add some text to a screenshot, please provide a screenshot annotated to the best of your ability, *as well as an unmarked copy of the screenshot*. This empowers our clients to redesign them according to their own branding if desired.

If you don't already have a preference, we suggest using any of the following tools:

* [dbdiagram.io](https://dbdiagram.io/home)
* [Excalidraw](https://excalidraw.com/) 
* [Google Drawings](https://docs.google.com/drawings/d/1xQa6fd3tTxo5iF9sAq4ynEs-6b4n-gvh14kXEkCvyW0/edit)
* [](https://mermaid-js.github.io/mermaid/#/)[Mermaid-JS](https://mermaid-js.github.io/mermaid/#/)
* [Lucidchart](https://www.lucidchart.com/pages)

These are also all great options for any rough architectural diagrams you may need to make.

#### [](https://www.lucidchart.com/pages)Upload Images to [Imgur](https://imgur.com/)

If you have screenshots or diagrams in your article, upload them to [Imgur's free image hosting service](https://imgur.com/) and embed them using Markdown. Include descriptive text inside the brackets (`[...]`) so that screen readers can describe the image.

Good:

> !\[A diagram showing different computer hardware](https://i.imgur.com/hBE7ZF8.jpg)

Bad:

> !\[](https://www.my-private-image-server.net/image-1.png)

#### Use Headers to Break Up Sections

Headers make your content more scannable. Use `##`, `###`, and `####` header tags to denote different sections. Headings should be written in [title case](https://apastyle.apa.org/style-grammar-guidelines/capitalization/title-case).

Good:

> \## How to Use JSON Fields in Your Python Application
>
> ...
>
> \### The Two JSON Formats Supported by Postgres
>
> ...

Bad (not title case):

> \## How to use JSON fields in your Python application
>
> ...
>
> ### The two JSON formats supported by Postgres
>
> ...

#### Denote Code with Backticks

Use code blocks when the code is one or more lines long or deserves special emphasis.

Good:

> \`\``
>
> function snafu() {
>
>   return null;
>
> }
>
> \`\``

Bad:

> `function snafu() { 
>
>   return null;
>
> }`

Use inline code when referring to a variable name or short command in context.

Good:

> Call the \`snafu()\` method to exit and return to your command line.

Bad:

> Call the "snafu()" method to exit and return to your command line.

#### Use Double Quotes for Quotations

Use blockquotes when the quote is two or more lines long.

Good:

> Some text leading up to the quote.
>
> \> "The field/element/path extraction operators return NULL, rather than failing, if the JSON input does not have the right structure to match the request; for example if no such key or array element exists."
>
> Some text after the quote.

Bad:

> Some text leading up to the quote. "The field/element/path extraction operators return NULL, rather than failing, if the JSON input does not have the right structure to match the request; for example if no such key or array element exists." Some text after the quote.

Use inline quotes when the quote is relatively short or when you're referencing a single word or phrase.

Good:

> "There's nothing to see here," said Davies.

Bad:

> \> "There's nothing to see here." - Davies

#### Use Emphasis Sparingly

Use *italics* to emphasize text or use **bold** to suggest strong emphasis.

Good:

> There is \*nothing\* as important as using \*\*spaces\*\* to indent your code.

### Communication

#### Communicate Delays and Roadblocks to Your Editor Proactively

You will not be penalized for late work if you've been in communication with us about the assignment. We can offer technical help and extensions, but you must ask two or more days before the due date.

Good:

> Hey Karl,
>
> I know the Postgres article is due next week, but I'm running into trouble. Would you be willing to hop on a quick call and explain the JSON fields in Postgres? Or do you have any resources that might help me out?

Bad:

> Hey Karl,
>
> I know my Postgres article was due today, but I'm not able to figure out the JSON fields in Postgres. Could I have an extension until next week to struggle with it more?

Authors that miss deadlines without communicating will not be eligible for future assignments.

#### Check Your Email When You Have an Open Assignment

While you have an open assignment, you should respond to emails within 48 hours unless you've notified us of your unavailability. If the assignment is overdue, you should respond within 24 hours.

Good:

> Hey Karl,
>
> Thanks for the update on this article. I'll keep that in mind while I'm working on the piece this weekend.

Bad:

> Hey Karl,
>
> Sorry, but I didn't see your email until today and I know the article is due now. I'll try to incorporate your feedback before midnight if I can.

Authors that fail to respond to emails about open assignments will not be eligible for future assignments.

## Final Notes

Creating [high-quality technical content](https://draft.dev/learn/technical-content) requires consistency and clear expectations. While having a style guide may not be necessary during your blog's early days, it's an invaluable asset as you grow.

Now that you've seen our style guide, I'd love to hear from you. If you have questions about an article you're writing, email [karl@draft.dev](mailto:karl@draft.dev) for help. If you'd like to talk about creating content for your blog, you can [schedule a call with me here](https://draft.dev/call).