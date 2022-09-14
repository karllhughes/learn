---
layout: post
title: What is Developer Experience?
description: Developer experience (DX) is about improving the developers'
  overall feelings toward tools or applications when building their own
  solutions. Good developer experience is reflected by how quickly a developer
  can build something new.
categories: developer-marketing
cta: Playbook
author: alexandre
date: 2022-09-14T18:10:29.794Z
img: /assets/posts/3258_draftdev_what-is-developer-experience_1200x2280_option-1-1-.png
---
Developer experience (DX) is about improving the developers' overall feelings toward tools or applications when building their own solutions. Good developer experience is reflected by how quickly a developer can build something new.

Developers are happy when they can quickly build a solution, create new features, and improve their customers' experience. DX has become a key element in gaining traction for your product. Building and shipping an API or tool is not enough—it needs to be able to scale, bring velocity, and gather approval from the developer communities.

The key question is, what does implementing a good developer experience mean?

This guide teaches how to provide developers with what they need. You will learn how to make your internal tools and products more accessible, useful, and approachable through developer-experience best practices.

## What Is Developer Experience All About?

The developer experience (DX) design process was inspired by [user experience (UX)](https://charcoal.marketing/blog/ux-design-a-real-thing-or-just-a-pretentious-buzzword) and aims to improve user, or developer, interaction with technological products. In short, DX is a branch of UX design where the "users" are developers. In practical terms, it's more of a set of best practices and tools derived from the UX process.

The lessons companies drew from UX is that the web was growing in both features and complexity. As a result, the focus on simple, rich, and user-focused features became a competitive advantage. The same is true whether your service is an API or a product targeting the developer audience. If you make that extra effort and think about the user first, you will gain an advantage over your competitors.

Developer experience is twofold: on one side, you have your internal developer working on creating your product's subsystems; on the other, you have other developers consuming your product.

You're unlikely to succeed in one without the other. As a matter of fact, many great products are born as internal tools, such as [Angular](https://www.angularjswiki.com/angular/history-of-angularjs/) or [Docker](https://www.infoworld.com/article/3204171/what-is-docker-the-spark-for-the-container-revolution.html). Because of their great value and developer experience, they got adopted quickly once released to the public.

![Developer experience is everywhere, both internal and external](https://i.imgur.com/GezYLYq.png)

However, no matter which developer we are talking about, providing a good developer experience relies on the same principles: usability, support, and documentation.

Imagining the flow of steps developers take on either side of the equation to accomplish their goals and how to make that flow as smooth as possible is a good place to start. For example, when you're building a product internally and want other developers who work on other applications and products to reuse what you have built as a company, you need documentation and tutorials that clearly explain how to use this product.

## How Can You Build a Great Developer Experience?

As mentioned, DX is about making developers feel good about using a tool or product. In practice, this involves the following:

* Improving product usability, so intuition alone helps developers code
* Providing support when they need it, so they never get stuck
* Writing great documentation, so that developers can learn by themselves
* Leveraging UX research to integrate those concerns early in the process

### Make the Product Easy to Implement and Integrate

The fundamental principle underlying developer experience is usability. If developers find your API or SDK easy to use when building applications, they will continue using your product and keep building with it.

You should do everything in your power to ensure that someone from a different company or another part of your organization can access and understand how they need to work with your technology without needing someone else on hand or documentation as an intermediary.

Easy implementation can be as simple as providing good autocompletion in a command-line interface and clearly naming your function and arguments in your SDK. But most importantly, you need to embrace established standards and strictly follow them.

- REST has become the standard for APIs, so the [proper implementation of the REST](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design) philosophy is expected.
- Infrastructure as code is the preferred way to configure almost anything. Therefore, you should provide dedicated APIs for provisioning and configuration. You could also supply a Terraform provider when relevant.
- Provide webhooks to notify developers about what is happening on your side of the system; this will enable other developers to integrate your product into CI/CD pipelines or monitoring and alerting systems.

Ultimately, you want your product to integrate easily into your developers' existing ecosystem. This is why standards and integration with common tools are so important.

### Provide Different Levels of Support

Communication with your developers is essential. There are three ways to establish a long-lasting connection with a developer and improve their experience.

The first approach involves providing support channels for developers to ask questions and get answers, such as forums, email contacts, and chat support. You can also embrace the open source model and use a public GitHub repository where developers can engage with the community by reporting issues and submitting pull requests to improve your product.

The second solution relies on developer advocates or evangelists. Companies like [Google](https://cloud.google.com/developers/advocates) and [Datadog](https://www.datadoghq.com/careers/detail/?gh_jid=4179649#:~:text=We%20are%20a%20growing%20global,delivering%20high%20impact%2C%20quality%20content.) have teams of developer advocates who are trained, knowledgeable, and available to support developers. They usually build demos or proofs of concept and talk at conferences to promote awareness of your product. They also engage with the community on social media (Twitter, LinkedIn, Reddit, etc.).

Finally, developers often look for experts in the field who can answer their questions and point them to resources. This is where professional services come into play. Companies like [MongoDB](https://www.mongodb.com/products/consulting) or [AWS](https://aws.amazon.com/professional-services/) provide access to experts that will design tailor-made workshops and solve the most complicated technical problems hand to hand.

### Create Great Documentation

Supporting developers would be a daunting task without proper documentation, as your team would need to personally answer these questions. So, writing good documentation is where most companies need to start. Developers need to be able to find answers efficiently without requesting your support. So you should focus on producing quality content for developers.

Most companies face [some level of issues with documentation](https://document360.com/blog/challenges-in-technical-writing/), not because they don't try hard to document everything they are building but because they don't know what type of content to create or how to organize it.

[Daniel Procida's documentation system](https://www.writethedocs.org/videos/eu/2017/the-four-kinds-of-documentation-and-why-you-need-to-understand-what-they-are-daniele-procida/) approach is particularly effective in building and organizing content. This system states that there are four types of content within documentation that have specific functions for developers: tutorials, how-to guides, technical references, and explanations.

- *Tutorials* are great at getting developers started. They are a key element of the developer experience.
- *How-to guides* teach developers how to solve a particular problem.
- *Technical references* (like OpenAPI documentation) *exhaustively* describe everything your API or tools can do.
- *Explanations* make the case around your technical decision and aim to persuade a developer that it's the best solution.

### Use Modern UI/UX Standards

Although developer experience is derived from user experience, not all UI/UX standards are relevant for delivering the best developer experience.

UX can be tricky to get right. You're not the user, so you can't know what they want. At the same time, you can't simply ask them and implement whichever feature they request. As  [UX practitioners well know](https://www.akendi.com/blog/its-true-users-dont-know-what-they-want/), users don't really know what they want either. Getting a clearly articulated answer from a user that leads you to the perfect design is impossible.

That's where user research comes into play. User research is an iterative loop involving the potential user—in our case, the developer.

First, you need to know what actions your user usually takes to accomplish a given task. Ask as many questions as possible to collect data (when, how often, why, etc.). Look for trends and patterns in user responses. Once you have collected data and identified those elements, design a prototype and try to confirm your finding with the user. If a prototype is successfully implemented, make it a full-fledged feature for your API or developer tool.

This approach provides a good starting point when you're unsure how to implement a feature and helps you avoid assumptions about what the user wants. In the developer experience world, alpha and beta releases are great solutions to conduct user research. Having developers use these early releases increases the chance that the feature shipped into the stable version will improve the developer experience.

## Conclusion

Developer experience (DX) is all about improving how a developer interacts with your product, including usability, support, and documentation. To ensure each of those three interactions has the strongest impact, you need to rely on the user-experience principles, particularly user research. But before that, you can already do many things to improve the developer experience.

In terms of usability, follow established standards to enable you to engage with the product without further help from the documentation or support.

In terms of support, you need to build a strong community through traditional support channels or proven strategies like developer advocacy and professional services.

In terms of documentation, a good structure is as important as the content itself. You need to provide developers with any resources they need to build with or on top of your product.

If you want to create a great developer experience and high-quality technical content that resonates with software developers, [Draft.dev](https://draft.dev/), a technical-content agency, can help you with regular content ranging from tutorials, guides, roundups, and persuasion articles written by experts in the field.
