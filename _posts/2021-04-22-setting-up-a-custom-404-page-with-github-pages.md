---
layout: post
title: Setting Up a Custom 404 Page with GitHub Pages
description: Learn how to set up custom 404 pages in GitHub Pages
categories: platforms
author: sodeeq
date: 2021-04-22T15:36:50.686Z
img: /assets/posts/lfropbg.png
---

In this article, I'll be showing you how to create a custom error 404 page in [GitHub Pages](https://lab.github.com/githubtraining/github-pages), a static site hosting service that allows you to publish and host your web pages through GitHub.

To break that down quickly: a static site is a website made up entirely of HTML, CSS, and JavaScript files. Everything the site needs to render is contained within these files, so there’s no need for server technology like PHP, Node.js, or Python. If the static site needs extra data from a server, it makes an asynchronous HTTP request with tools like `[fetch api](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)` or `[axios](https://github.com/axios/axios)`. And you’ll probably want to make sure that static site has a 404 page.

Displaying a 404 error page on your site is sort of like delivering bad news—the tone and manner of your delivery can determine if the person receiving the news will either be upset or be ready to agreeably look for another solution. Fortunately, GitHub Pages makes creating one a walk in the park.

## How Does GitHub Pages Work?

Hosting your site on GitHub Pages is as easy as signing into GitHub and creating a new repository. 

![Create a new GitHub repository](https://i.imgur.com/kI4Tuh6.png)

Your repo name should have the following format: `<your github username>.github.io`.

![Name your GitHub.io repo](https://imgur.com/33fezEh.png)

Add files to your repo. You can do this either by creating the files locally and pushing to remote or by creating the files directly on GitHub.

Go to the Settings tab of your newly created repository.

![Click Settings tab](https://imgur.com/O3szeWF.png)

Scroll down to the GitHub Pages section. 

Here, you can choose the branch you want to serve your pages from, the root directory, and even select a Jekyll theme. If you already have a custom domain name, you can add it here.

By adding a custom domain name, you can access your site using `[yourdomainname](http://example.com)` instead of your `[github.io](http://github.io)` domain.

![GitHub Pages settings](https://imgur.com/JKGXKmS.png)

That’s all! Your site is now ready to be published. Visit `<your github username>.github.io` to see your new website. 

You can make changes to your site whenever you choose. They become available immediately after you push/merge to the branch you’ve chosen to serve your pages from.

Using GitHub Pages for your static site gives you some nice benefits:

- GitHub Pages is free to use. No coughing up extra cash just to host some basic web pages.
- You can use it to host websites like single-page applications or blogs.
- You can add a custom domain name to your site.
- You can enable HTTPS for your domain in just one click.
- You get the added advantage of managing your site with Git. Version-controlling your website becomes a piece of cake.

## Why Is a 404 Page Important?

The 404 page is a famously dreaded sight across the internet. It’s a page that neither website users nor owners like to see, but it’s an unavoidable one. Its purpose is to inform a user that the page they’re looking for doesn’t exist.

Think about it: it isn't every time you go into a store that you find everything you're looking for. Certain items may be sold out or perhaps the store never sold them to begin with. That’s exactly what happens on the web. Perhaps the page’s URL changed, breaking an old link, or maybe the page was removed altogether. A user could have manually input the wrong URL to begin with. However a user has arrived at a particular URL, the requested web page doesn't exist.

Specifically, **404** is an [HTTP status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for a "Resource Not Found" or simply "Not Found" error. It applies to all kinds of resources on the web, including HTML files, CSS files, JavaScript files, documents, images, and just about any other file that could be requested from a server.

How you as the webmaster choose to convey a 404 error is very important. It can either improve your user’s experience on your site or make it worse.

## What Makes a Good 404 Page?

At the end of the day, what’s on your 404 page is up to you, but I can give you a few tips to make it as palatable as possible for your users:

- First and foremost, a 404 page should return with an actual 404 HTTP status code. This is important so web crawlers like Google's bot don’t incorrectly index an erroneous page as a valid page, as this can negatively impact your SEO.
- The 404 page should make it clear to the user that there's a problem. This can be achieved by making the **404** or **Not Found** message prominent on the page.
- The page should offer a way out to the user. Unless you want the user stuck on your error page or want them to close your site immediately, your 404 page should provide them with a means to navigate away from the page. Add an obvious link to your site's homepage to somewhere on the error page, or you can suggest links to pages that might be similar to what the user was looking for in the first place.
- You can provide a way for users to report a broken page, enabling you to quickly fix any issues.
- Add a search bar for users to find other things they might be looking for.
- Make the design pleasing to the eye. A 404 page is still a part of your website, so you should put as much thought into its design as you have for other valid pages. The page should carry elements of your brand, and not look like a desert island.

GitHub's very own 404 page is a good example of what a 404 page should look like. The error code and message are both prominent on the page, and there's a search bar to help you find other content.

![GitHub’s error 404 page](https://imgur.com/lNsDCam.png “GitHub's 404 page”)

If you don’t add a custom 404 page to your GitHub Pages site, then by default GitHub displays the following 404 page:

![GitHub Pages default 404 page](https://imgur.com/SrpHh2H.png “Default GitHub Pages 404 page”)

Not bad, eh? But not good enough for your brand.

## How to Create a Custom 404 Page in GitHub Pages

Fortunately, GitHub also understands the importance of a 404 error page, and provides developers an easy way to add one to their GitHub-hosted pages. Let's look at how you can add your own custom 404 page.

Create a new file in the root of your repository and name it `404.html`.

![Add file to repo](https://imgur.com/q5x4MeZ.png)

![Name 404 page](https://imgur.com/pQpMVoQ.png)

Then go on to add content for the 404 page as follows:

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Not Found</title>
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link href="https://fonts.googleapis.com/css2?family=Chango&family=Roboto:wght@300&display=swap" rel="stylesheet">
    <style>
        body{
            background-image: url("https://images.unsplash.com/photo-1616235132417-99f443954d2e?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=334&q=80");
            background-size: cover;
            font-family: 'Roboto', 'sans-serif';
        }
        main{
            display: flex;
            height: 100vh;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }
        .header404{
            font-family: 'Chango', cursive;
            font-size: 48px;
        }
        .content404{
            text-align: center;
        }
    </style>
</head>
<body>
    <main>
        <h4 class="header404">404</h4>
        <div class="content-404">
            Uh-oh! We couldn't find the page you are looking for.
        </div>
        <p>
            <a href="/">Check our home page</a>
        </p>
    </main>
    
</body>
</html>
```

Commit your changes, then try to visit a page that doesn't exist on your site, eg,`username.github.io/a-random-page-that-doesn't exist`. A page like this should appear:

![Custom error 404 page design](https://imgur.com/tl4s7e8.png “Custom error 404 page”)

### Conclusion

Hopefully, this article has shed some light on the importance of a 404 page and why you should put some effort into branding it as you would other pages of your website. When properly done, a 404 error page can be a good way to increase your website's conversion rate.

Unlike many other host servers where you have to tinker with `.htaccess` or other kinds of configuration settings to handle 404 error pages, GitHub Pages makes it incredibly easy. All you need to do is add a single file, and you’re good to go.

If you’re stuck for ideas on what your 404 error page can look like, you can always [look around for some 404 inspiration](https://www.creativebloq.com/web-design/best-404-pages-812505).
