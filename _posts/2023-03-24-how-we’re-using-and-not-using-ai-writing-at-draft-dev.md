---
layout: post
title: How We’re Using (and Not Using) AI Writing at Draft.dev
description: We believe in embracing new technology and learning how to use it.
  In their current state, AI writing tools cannot replace the writers we work
  with (engineers with deep subject matter expertise), but we are exploring
  these tools and how using them could make sense.
categories: processes
cta: Call
author: karl
date: 2023-03-24T18:07:27.597Z
img: /assets/posts/robot-typewriter.jpg
---
In 2020, I started exploring AI writing tools. I recorded a screencast back then on [how you could use GPT-3 to create or at least help you create a technical blog post](https://www.youtube.com/watch?v=lywWkR0vo_A). In 2021, I recorded a more [in-depth comparison of the AI writing tools available at that time](https://www.youtube.com/watch?v=UO6YATnEFGU&t=18s).

It’s interesting to compare the two videos because you can see how much better these tools got in just a year. That said, all the tools I tried in 2020 and 2021 were clunky. They seemed to push in the direction of writing entire blog posts for you, but they couldn’t get beyond surface-level definitions of terms and often introduced factual inaccuracies.

In 2022, [OpenAI released Chat GPT](https://chat.openai.com/), and by early 2023, it had hit the mainstream. Everyone from clients to writers to family members asks me about AI writing now, so I thought it would be worth putting down a short summary of my thoughts and the role we see these tools playing at Draft.dev.

**TL;DR: We believe in embracing new technology and learning how to use it. In their current state, AI writing tools cannot replace the writers we work with (engineers with deep subject matter expertise), but we are exploring these tools and how using them could make sense.**

## A Brief History of AI Writing Tools

The well-known generative writing tools available today (like GPT-3 and more recently, GPT-4) use [large language models (LLMs)](https://blogs.nvidia.com/blog/2023/01/26/what-are-large-language-models-used-for/) to summarize or generate text based on existing text datasets. In other words, they “read” content on the internet and use it to surmise patterns that allow them to write new content.

LLMs are a form of neural network, a concept that’s been part of machine learning for at least 40 years, but the big unlock in recent years has been cheaper access to computing power and storage. While it’s not trivial to crawl enough of the internet to build one of these things, Google’s been doing it since 1996, and as you might imagine, they’re not the only ones gathering data.

As the ability to collect and store text data improved, so did the availability of computing power to compute the strength between nodes in this data. The technical details go beyond my understanding, but essentially, LLMs today are trained on **trillions** of words to calculate the relationship between them and “learn” to use them.

## AI Writing Today

This technology is changing (and improving) rapidly, but as of March 2023 when I write this, the best general-purpose consumer-available AI writing tool is [OpenAI’s GPT-4](https://openai.com/research/gpt-4) (the model used by Chat GPT).

It can do amazing things like write a short poem about the recent collapse of Silicon Valley Bank in the style of Charles Bukowski:

```
The Valley once glittered with gold,
But greed took hold, and fortunes were sold.
Silicon dreams turned into a nightmare,
As the bank collapsed, leaving despair.

Investors panicked, accounts were drained,
The system failed, and hope remained.
Bukowski saw it all before,
The rise and fall of money's allure.

The Valley's tech giants brought hope and change,
But the price we paid was out of range.
The crash of '23 was a bitter pill,
And the wounds may take years to heal.

But in the rubble, we'll rebuild anew,
The spirit of innovation shining through.
Lessons learned, the future bright,
As we rise again with all our might.
```

Or describe the feeling that an ancient Greek stoic would have while falling off a cliff:

```
I strive to maintain a state of inner calm and rationality regardless of external circumstances. Therefore, as I fall off a cliff, I focus on accepting the inevitability of my fate rather than giving in to fear or panic.

I remind myself that death is a natural part of the cycle of life, and that my consciousness will simply return to the universe in a different form. I reflect on the impermanence of all things and the idea that my time on this earth was always limited. I find solace in the knowledge that I lived a virtuous life, true to my principles and values.

As I approach the ground, I feel a sense of detachment from my physical body and a deep sense of peace. I trust that the universe has a plan for me, and that whatever happens next is simply part of that plan. In this moment, I am at peace with my fate, knowing that I lived and died according to my own code of ethics.
```

### What AI Writing Doesn’t Do Well

But it’s not perfect. The current iteration of GPT-4 isn’t updated with real-time data ([although that’s coming soon](https://news.ycombinator.com/item?id=35285664)), and it often states factual inaccuracies confidently without citing sources, so it’s essential to have a human in the loop.

> "AI experts caution, however, that such tools should only be used to support people who are already experts in their domain. Generative AI has been shown to spew disturbing content and misinformation, while other concerns have surfaced over intellectual property theft and privacy." - [Karen Hao, *The Wall Street Journal*](https://www.wsj.com/articles/from-ceos-to-coders-employees-experiment-with-new-ai-programs-32e1768a)

It also doesn’t do well with personal experience or realistic examples, especially in niche topic areas (like ours). While you can try to push it to do so, it doesn’t always understand “real life” so it struggles to replicate the human experience.

Finally, it doesn’t do well with extended pieces of text. It struggles to go deeper into topics, so you’ll often find it repeating the same surface-level definition of a topic or spitting out nonsensical jargon because it doesn’t have enough good data on a particular niche.

For these reasons, it struggles at technical depth—one of our main selling points to clients—and it’s nowhere close to replacing our world-class group of software engineers as a writer. As a rule, we push writers to go deeper and add more personal experience when we see it lacking, and we’re planning to use [Positional](https://www.positional.com/) to detect AI-written content going forward.

### What AI Writing Does Do Well

That said, we are starting to use GPT-3 in a few specific ways.

We’ve started using it to generate short descriptions of new articles, new variations of titles for blog posts, and even some article outlines. While we still have to guide and fact-check the machine, it’s saving us a few hours of work per week already.

Coworkers have told me they use it to reply to emails, come up with definitions for generic terms, and get started on new ideas. While I haven’t found it useful for writing the actual content of a blog post, it has helped me come up with ideas for items in a list or brainstorm transitions between sections.

Many of GPT-3’s weaknesses are fixable though, so I think we’ll continue using it more in the future. It’s pretty easy to imagine OpenAI including fact-checking and real-time data in future models. Other companies will also be building specialized versions of OpenAI’s generic language models to work better for internal docs, emails, and industry-specific writing. It’s going to be a very interesting next few years in the writing industry.

## The Eventual Future

**AI writing tools will be for writers like Excel is for accountants.**

Great writers (like great accountants) won’t be replaced by AI writers, but will instead learn to work with AI as a virtual assistant to get more done.

Subject matter experts with personal experience and knowledge of the nuance of their field won’t be replaced by AI, but maybe the tools will make writing more approachable. I’d love to see more engineers start writing because tools like Chat GPT make it easier.

Generative AI might also change the way we search for information online. We may be able to interact with search engines through more natural formats like asking questions, and maybe…just maybe…[Siri will finally be good at something](https://www.youtube.com/watch?v=SEg4rl1B7HI).

Like [Ryan Law recently said](https://twitter.com/thinking_slow/status/1626175493664919553?t=vn_6mrMd1OvQQcwG9aAZCA&s=19), anyone working in content marketing or writing today should be exploring these tools and learning how to use them in their day-to-day. I’d love to hear how you’re exploring and using AI in your writing. [Find me on Twitter](https://twitter.com/karllhughes) to continue the conversation.


