---
layout: post
title: Markdown Writing and How to Use it
description: "If you don't know what Markdown is, or if you've only heard of it,
  it may seem confusing how a tool for writing can do these things and be held
  in such high regard by an entire community. This blog post will dive a bit
  deeper into why Markdown was developed, what exactly it is, and why you should
  use it. "
categories: processses
cta: Playbook
author: kasper
date: 2021-12-03T00:30:09.590Z
img: /assets/posts/artem-sapegin-derxvssqndm-unsplash.jpg
---
If you’ve spent even just a small amount of time in the engineering world, you will have come across Markdown. It’s quickly become the de-facto standard for any writing project within engineering. Many favor writing in Markdown, whether it be a simple README file to explain what a certain application does or complete documentation. It makes it easy to write readable, styled documents that you can read directly or after parsing through a Markdown-to-HTML converter.

If you don’t know what Markdown is, or if you’ve only heard of it, it may seem confusing how a tool for writing can do these things and be held in such high regard by an entire community. This blog post will dive a bit deeper into why Markdown was developed, what exactly it is, and why you should use it. To give you an idea of how you can use Markdown, even this blog post is done in  Markdown writing.

![](https://lh3.googleusercontent.com/O7es7KyvPhtmP4cLa0uZwR1q3RsKUdg9PbJJkFui1tqHxxgmokQK7lRE9saywqmNiJpJPpwpz4ZseZOLSn2PKPqWVqcQwhgSUH6PTRv9Fgy31OfFTVNJnEIBTfZwrMKaFtCLF23y)

# A Brief History of Markdown

As with anything, to truly understand it, you need to understand why it exists. This applies when understanding how to use Markdown.

Way back when people were first starting to use written text on computers, people quickly wanted a way to express themselves. Whether by emphasizing some words more than others or writing ordered lists using hyphens, the simple plain text didn't cut it. One of the earliest examples of text formatting was to surround a word with asterisks to make it *italicized*, something that's still in use in Markdown writing today.

As time went on and websites became more popular, pure black text on a white background wasn't good enough. It had to be styled, which you could do with a combination of HTML and CSS. However, writing the tags needed in HTML added a lot of extra work, so WYSIWYG editors started appearing. What You See Is What You Get. Editors that provided writers with buttons to help format text.

This worked great and is still in use in many places today. However, some weren't satisfied. The fact that you couldn't simply be writing text but instead had to use either complicated keyboard shortcuts, or point-and-click interfaces, was a nuisance for many. This was when people started creating alternatives. Ways of writing text that could then be directly converted into HTML. Using the old email conversations as inspiration, these tools wanted it to be possible to create a styled article, using only characters found on your keyboard like asterisks, hyphens, underscores, etc.

Many alternatives were created, like atx and textile, but Markdown became the one widely used in the end. It allowed writers to write more naturally, not thinking about removing their hands from the keyboard, using only regular characters for the formatting, while still being readable in its plain-text format. You can read [this article](https://capiche.com/e/markdown-history) to learn more about the history.

# Why Use Markdown?

The history should indicate why Markdown became popular and why it's still in use today. Over time many people have used rich text editors, so-called WYSIWYG editors, where the quickest way to format your text is by using keyboard shortcuts or buttons. This takes focus away from writing. As stated earlier, Markdown uses familiar characters to format your text, making it possible for formatting to become just as much second nature as the writing itself.

So, it makes writing and formatting easier, but that’s far from the only reason to start using Markdown. It also makes your written content more flexible. As stated in the introduction, this article is written using Markdown. You see the written text after it’s been converted into HTML, making the headers and the text styled in a specific way. If you were to take the original Markdown text and paste it into another editor, it would look slightly different. The formatting will be the same, meaning italicized words will still be italicized, but the headers may be different in size, color, or even font.

The formatting stays the same, but the style can be changed. That's the power of Markdown. That is why we use it here at Draft.dev when working with clients and writers. It allows us to not worry about how a paragraph needs to be styled according to a specific client's blog. It will enable us to stay focused on the quality of the content instead of the design.

# Writing in Markdown

Now that you’re, hopefully, convinced that writing in Markdown is the easiest way to produce flexible content, it’s time to learn it. Luckily, one of the significant strengths in learning  Markdown is how quick it is to pick it up. Writing headers is done by using hashtags. For example, this section is written like so:

```md
# Writing with Markdown

Now that...
```

If you want to make subheaders, it's just a matter of adding more hashtags.

```md
# Header 1

## Header 2

### Header 3
```

That's how easy Markdown makes the process of creating new sections. Styling text within a single section is a matter of surrounding the words with the correct characters. The following section:

```md
> This sentence contains a _italized_ word

> This sentence contains a **bold** word

> This sentence contains a [url](https://example.com)
```

Turns into the following, where the `>` characters create the indentation:

> This sentence contains an *italized* word
>
> This sentence contains a **bold** word
>
> This sentence contains a [url](https://example.com)

As you can see, the characters in using Markdown may seem a bit weird at first, but once you’ve gotten used to them, you can quickly write formatted text. To learn markdown in more detail, you can use [this interactive tutorial](https://www.markdowntutorial.com/). You may have noticed that italicizing a word was done differently in this example than shown earlier in the article. Markdown offers many different ways of doing the same thing, allowing the writer to express themselves the way that fits them best.

# Markdown Editor

Learning how to use  Markdown is one thing. Using it is another. However, the path between the points is not long. While a part of why Markdown is powerful is that it can be written in any text editor (even Notepad), it’s often helpful to use an editor that supports Markdown, enabling you to get a live preview of what you are writing. When writing this blog post, I’m currently using [VSCode](https://code.visualstudio.com/) with a few helpful Markdown extensions installed.

If you don't want to use VSCode, there are many other great alternatives, many even online. When I first started writing Markdown, I was a heavy user of [Dillinger](https://dillinger.io/). It's a straightforward interface, and you can begin writing in Markdown immediately.

Over time, I've found another tool called [StackEdit](https://stackedit.io/app#) which I prefer. I think the UI is smoother, and I like the preview function more. I'm mentioning both of them as everyone is different, and some will prefer one over the other. However, those two options are among the most popular to use.

# Conclusion

That’s really all you need to know about Markdown writing and how to use it. It’s a handy tool to have in your toolbelt, yet it’s not so complicated that you need to spend weeks learning it. I can only recommend that you start to learn Markdown by writing your content in it wherever possible. It’s universal, and once you know how to write Markdown, you’ll be surprised to find how many places it can be used.