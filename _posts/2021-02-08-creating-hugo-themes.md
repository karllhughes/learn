---
layout: post
title: Creating Hugo Themes
description: What is a Hugo Theme and why might you want one? We answer that
  here, and give a step-by-step to create your own.
categories: platforms
author: siddhant
date: 2021-02-08T18:19:06.799Z
img: /assets/posts/nsant7blac-2funtitled_artwork-204.png
---
Lately, developers are adopting static site generators like [Hugo](https://gohugo.io/) to quickly deliver content to their audience. Frameworks like these cut down on issues that pop up with scalability, version control, managing dependencies, and performance.

Hugo in particular offers tons of features right out of the box for creating fast, modern, and secure static websites. It's written in Go, a powerful server-side scripting language, and offers a clean workflow for creating landing pages, portfolios, documentation, or blogs without a lot of extra layers of complexity.

Hugo also has plenty of themes ready to go [right away](https://themes.gohugo.io/), but a prebuilt theme probably isn’t going to match your brand's vision. Most likely, you’re going to want a custom theme, something that affords you fine-grained control over things like color schemes, typography, and UI components.

In this article, I’ll walk you through how to quickly customize your Hugo site for your desired brand and aesthetic by building your own theme.

##  How to Create a Multi-author Hugo Blog Theme  
Specifically, I’ll demonstrate how to create a multi-author blog theme in Hugo. I’ll cover paginating multiple blog posts, adding tags or categories, setting up support for multiple authors, and adding some SEO considerations to give your site more presence on the web.

### Spinning Up a Site
Once you have Hugo installed (refer to the complete installation guide[ here](https://gohugo.io/getting-started/installing)) and a modern code editor (like [VS Code](https://code.visualstudio.com/)), you're ready to begin.  

1. In a directory of your choice, create a new Hugo site by running the following command:  

```shell  
hugo new site multiauthor-blog-site  
```  

2. Once a new Hugo project is created for you, navigate into the directory.   

```shell  
cd multiauthor-blog-site  
```  

3. Open the project in your editor and run the following command to spin a development server where you can see your changes live:  

```shell  
hugo server  
```  

### Creating a Theme
With your brand-new site up and running, it’s time to start customizing the canvas: 
 
1. Create a new theme inside the root directory by running `hugo new theme blog-theme`. This generates a folder called `blog-themes` inside the themes directory containing a bunch of files and folders. You'll mostly be working with two directories: `/blog-theme/layout`, where all your HTML files will be present, and `/blog-theme/static` for static assets like images, CSS styles, and custom JavaScript.

2. It’s time to tell Hugo that you'll be using this new theme for your site. Usually, those details go inside a configurational file `config.toml` in the root directory. Add a key `theme` with a value of your theme's name (ie, `blog-theme`) as shown: 

```toml  
baseURL = "http://example.org/"  
languageCode = "en-us"  
title = "My New Hugo Site"  
theme = "blog-theme"  
```   

3. Inside the `baseof.html` file (`theme/blog-theme/layouts/default/baseof.html`), add the following markup:  

```html  
<!DOCTYPE html>  
<html lang="{{ .Site.LanguageCode }}">  
    {{- partial "head.html" . -}}  
    <body>  
        {{- partial "header.html" . -}}  
        <main>  
        {{- block "main" . }}{{- end }}  
        </main>  
        {{- partial "footer.html" . -}}  
    </body>  
</html>  
```  

The previous code creates some semantic elements for your site and references a site variable from your `config.toml` file in Hugo's default templating language Go. If you look inside your `/theme/blog-theme/layouts/partials` folder, you'll find a `head.html` file containing all the markup for your site's `<head>` tag. Similarly, you can find a partial `footer.html` file to render a footer on your site.
   
The rest of the content of your site should go inside the `<main>` tags.

4. Add the following lines inside `/theme/blog-theme/layouts/index.html` to tell Hugo to insert the page content between the `<main>` tags in the `baseof.html` file:  

```go  
{{ define "main" }}  
{{ .Content }}  
{{ end }}  
```  

### Creating and Styling the Navbar  
The navigation bar allows users to easily visit different sections of your site.

1. Inside `/theme/blog-theme/layouts/partials`, you can find a `header.html` that acts as the default header for your site. Put all the HTML for the navbar inside this file. Hugo will automatically render it on your site.   

```html  
<header>  
    <nav class="navbar" role="navigation">  
        <div class="navbar__left">  
            <a href="/"><strong>blogsite.com</strong></a>  
        </div>  
        <div class="navbar__right">  
            <a href="/blog">Blogs</a>  
            <a href="/categories">Categories</a>  
        </div>  
    </nav>  
</header>  
```  

The `/` link is to direct the user to your site's homepage. You can leave the remaining links as it is for the moment.  

Your navbar could look better, so let’s walk through how to add custom CSS styling to your theme. The static folder inside your theme holds all the static content related to your theme, including custom styles for your templates. So all stylesheets pertaining to your theme go inside the `/theme/blog-theme/static/css` folder. 

2. Create a file called `style.css` and reference it inside your theme's `head.html` file (`/blog-theme/layouts/partials/head.html`) as shown:  

```html  
<link rel="stylesheet" href="/css/style.css" type="text/css" media="all" />  
```  

Hugo will push all your styles from this file onto your HTML pages.

You can create multiple stylesheets to break down your styles into logical modules. For brevity’s sake, let's keep all the styles for this project inside `style.css` only.  

```css  
body {  
    background-color: #fcfcfc;  
    color: #333;  
    font-size: 125%;  
    line-height: 1.5;  
    margin: 0 auto;  
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;  
  }  
  .content {  
    margin-bottom: 2rem;  
  }  
    
 .navbar{  
   display: flex;  
   align-items: center;  
   justify-content: space-between;  
   height: 25px;  
   background: gainsboro;  
   padding: 10px;  
 }  
 .navbar__right{  
   display: flex;  
 }  
  a{  
    text-decoration: none !important;  
    color: black;  
  }  
 .navbar__right a{  
   text-decoration: none;  
   font-size: 14px;  
   margin-right: 10px;  
   color: black;  
   transition: all 100ms;  
 }  
 .navbar__right a:hover{  
   text-decoration: underline;  
   font-weight: bold;  
 }  
 main{  
   margin: 0 200px;  
 }  
```  

You can easily style other pages following the same pattern.  

###  Adding, Organizing, and Listing Blogs  
All the markdown files for your site go inside the `content` folder in the root directory of your project. Hugo renders the main content for your homepage from an `_index.md` file inside the `content` directory.

1. Create an `_index.md` as shown:   

```markdown  
# Welcome to My Multi-Author Blog  
Hola, devs! Welcome to my site.  
```  

If you visit [http://localhost:1313](http://localhost:1313),  you can see a simple homepage for your site.  
 
![Screenshot of the homepage](https://imgur.com/0Bn2iBX.png)

2. Inside the `content` directory, create a `blogs` folder where you can organize your blog posts. You can segregate them further based on the year of publication. The following command creates a new blog post in the designated directory with some metadata:   

```shell  
hugo new /blog/2020/fundamentals-design-principles.md  
```  

3. Inside that file, add some dummy content:  

```markdown  
---  
title: "Fundamentals of Design Principles"  
date: 2020-12-27T22:37:51+05:30  
draft: true  
---  
![](https://images.unsplash.com/photo-1516638022313-53fa45a84c7f?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80)  
### Diving deeper into design principles and methodologies  
Lorem...  
```  

4. While you're at it, add a few more blogs with some content using the same process:  

```powershell  
hugo new /blog/2020/java-spring-mvc.md  
hugo new /blog/2020/hugo-themes.md  
```  

Hugo renders each individual blog post on the URL `/blog/2020/java-spring-mvc` by default. If you visit [http://localhost:1313/blog/2020/java-spring-mvc](http://localhost:1313/blog/2020/java-spring-mvc), you can see the specific blog post.   

Let's create a page for your theme that lists all the blogs and allows a user to navigate to a particular post.

1. Recall that the navbar contains a route directing to `/blogs`, so you can render a list of all the blogs when the user visits `/blogs`. Hugo has a default directory where it looks for list type pages; this is where you can create a generic template for any kind of lists you want to render.

2. Inside `/blog-theme/_default/list.html`, add the following code, which simply iterates over the `.Pages` variable that contains a list of all child pages for `/blogs`. Inside the `range` loop, the current context (or the dot`.`) is always an individual page that’s used to generate the customized link. 

```html  
{{ define "main" }}  
<div class="container">  
    <div class="section">  
        <div class="content">  
            <h1 class="title">{{ .Title }}</h1>  
            {{ .Content }}  
            {{ range .Pages }}  
            <ul>  
                <li><a href="{{ .Permalink }}">{{ .Title }}</a></li>  
            </ul>  
            {{ end }}  
        </div>  
    </div>  
</div>  
{{ end }}  
```  

Now, if you now go to [http://localhost:1313/blog](http://localhost:1313/blog), you will see a list of all your blogs. Navigate to each blog by clicking an item on the list.  

### Creating a Blog Post Template 
Next, let’s create a template for your theme that renders each new blog post exactly as you’d like it to appear.

1. Head over to the `layouts` folder (`/theme/blog-theme/layouts`) and create a folder named `blogs` with a file `single.html` inside it. This structure allows Hugo to render blogs faster, as it's higher in the lookup order with respect to the `single.html` file present in the `_default` (`/theme/blog-theme/layouts`) directory.   

```html  
{{ define "main" }}  
<section class="section">  
  <article>  
    <div class="blog__container">  
          <h1 class="blog__title">{{ .Title }}</h1>  
            <div class="blog__details">  
              <div class="author-image-container">  
                  <img src="" alt="author-image" />  
              </div>  
              <div class="blog__info">  
                <p>By  author name </p>  
                <p><time>{{ .PublishDate.Format "January 2, 2006" }}</time> |   
                    {{ .ReadingTime }} {{ if eq .ReadingTime 1 }} minute {{ else }} 	                         minutes {{ end }} read  
                 </p>  
              </div>  
              <div class="blog__categories">  
             	Blog categories  
              </div>  
            </div>  
          <div class="content">  
            {{ .Content }}  
          </div>  
        </div>  
  </article>  
</section>  
{{ end }}  
```  

The previous markup structures the contents of the blog post page by first rendering the blog's title, followed by metadata like author name, image, an average read time, and related content categories.

2. Let's style this markup:   

```css  
.author-image{  
  object-fit: cover;  
  border-radius: 50%;  
  width: 48px;  
  height: 48px;  
}  
.blog__title{  
  font-size: 32px !important;  
  font-weight: bolder;  
}  
.blog__details{  
  display: flex;  
  align-items: center;  
}  
.blog__info{  
  margin-left: 20px;  
  flex: 1;  
}  
.blog__info p{  
  margin-block-start: 2px;  
  margin-block-end: 2px;  
  font-size: 14px;  
}   
.blog__image > img{  
  height: auto;  
  width: 100%;  
  object-fit: contain;  
  margin: 10px 0;  
}  
.blog__categories{  
  display: flex;  
  align-items: center;  
}  
.category{  
  padding: 5px 5px;  
  background: #f07979;  
  font-size: 12px;  
  border-radius: 5px;  
  width: auto;  
  margin-right: 5px;  
}  
.category a{  
  color: #fff;  
}  
.content img{  
  height: auto;  
  width: 100%;  
  object-fit: contain;  
  margin: 10px 0;  
}  
```  

3. Go to `/blogs` and click on a blog post to see some structured content of that post. Since other details, like author information, haven't been hooked yet, you’ll only see some boilerplate text.

4. Add some hard-coded categories for your blogs inside the  `config.toml` file:  

```toml  
[params]  
    categories = ["Web Development","Blogging","Web Design"]  
```  

5. You can now simply loop over these categories and render them inside the `single.html`.  

### Adding Support for Multiple Authors  
Now your content is there, but there’s still no information about the author.

If you were building a single author template, you could create a variable for author name and image in the `config.toml` file and reference it inside the `single.html` file as you did for categories in the previous section. Since you want more than one author on your site, you need to add support for multiple authors in your theme.
1. Inside the root folder, head over to the `data` directory and create a JSON file with the name of the author (for example, `siddhantvarma.json`) with the following information in JSON format about the author:   

```json  
{  
    "name": "Siddhant Varma",  
    "bio": "Howdy Guys! I'm a React and JavaScript Developer from India. I love watching 			 movies and creating content for developers",  
    "avatar": "/img/authors/siddhantvarma.jpeg",  
    "social": {  
        "linkedin":"https://www.linkedin.com/in/siddhantvarma99/"  
    }  
}  
``` 

2. Add more author information to your preference, like social media handles and external sites. You can use the following structure to organize your authors: 

```  
├── data  
	└──authors  
		└── siddhantvarma.json  
		└── sammills.json  
		└── randylev.json  
```  

3. Create as many authors as you like. Add an `author` key and value pair inside the metadata for each post as shown to associate an author with a particular blog post/ Yyou must ensure that the author's name matches exactly the name of the JSON file for that author. 

```markdown  
---  
title: "Java Spring MVC"  
date: 2020-12-27T20:08:49+05:30  
author: randylev  
---  
```  

Now each blog post is associated with a JSON file describing some details about that post's author. 

4. You can go back to `single.html` and render the author properties on the page along with the categories added in the previous section.  

```html  
{{ define "main" }}  
<section class="section">  
  <article>  
    <div class="blog__container">  
      {{ $author := index .Site.Data.authors (.Params.author | default "default") }}  
          <h1 class="blog__title">{{ .Title }}</h1>  
            <div class="blog__details">  
              <div class="author-image-container">  
                <img src="{{ $author.avatar }}" class="author-image">  
              </div>  
              <div class="blog__info">  
                <p>By   
                  {{- if $author -}}  
                      {{ $author.name }}  
                  {{- end -}}  
                </p>  
                <p><time>{{ .PublishDate.Format "January 2, 2006" }}</time> |   
                    {{ .ReadingTime }} {{ if eq .ReadingTime 1 }} minute {{ else }} minutes {{ end }} read</p>  
              </div>  
              <div class="blog__categories">  
                {{ range $idx, $category := .Site.Params.categories }}  
                  <div class="category"><a href="{{ "categories/" | relURL }}{{ $category | urlize }}">{{ $category }}</a></div>  
                {{- end }}  
              </div>  
            </div>  
          <div class="content">  
            {{ .Content }}  
          </div>  
        </div>  
  </article>  
</section>  
{{ end }}  
```  

And there's your blog with some content, metadata, an author image, and categories. You can easily navigate to other blog posts and see how various author information is rendered.

![Your blog post template](https://imgur.com/zNyxaRT.png)  

### Implementing Pagination  
Ensure good user experience on your site by allowing a user to easily paginate through the blog posts. Hugo offers this feature right out of the box by providing the variables `.PrevInSection` and `.NextInSection`. These link to the previous and next page objects to implement simple pagination for your theme.

The following code renders two buttons at the end of each post and directs the user to the immediate previous and next post with respect to the current post. 

```html  
    <div class="blog__navigate">  
      <div class="blog__navigateButtons">  
        <div class="blog__navigateButtons__previous">  
          {{ with .PrevInSection }}  
          <button><a href="{{ .Permalink }}">&#8592; Previous Post: {{ .Title }}</a>   	           </button>  
          {{ end }}  
        </div>  
        <div class="blog__navigateButtons__next">  
          {{ with .NextInSection }}  
          <button><a href="{{ .Permalink }}">Next Post: {{ .Title }} &#8594;</a></button>  
        {{ end }}  
        </div>  
      </div>  
  </div>  
```  

Let's style this layout inside `style.css`:  

```css  
.blog__navigateButtons{  
  display: flex;  
  justify-content: space-between;  
  align-items: center;  
}  
  
.blog__navigate{  
  margin-bottom: 20px;  
}  
.blog__navigate button{  
  border: none;  
  outline: none;  
  background: rgb(88, 123, 240);  
  color: #fff;  
  padding: 10px 20px;  
  border-radius: 5px;  
  cursor: pointer;  
  transition: all 200ms;  
}  
.blog__navigate button:hover{  
  transform: translateY(1.5);  
  background: rgb(43, 92, 226);  
}  
.blog__navigate a{  
  color: #fff;  
}  
```  

Now you have a set of fully functional pagination buttons at the end of each post.

![Pagination buttons for a Hugo theme](https://imgur.com/OazK4ly.png)  

### Creating a Category Page  
Categories are common on blogs for easy discovery of similar posts on your site.  You already have some predefined categories inside `config.toml` file, so let's create a separate category page that lists out all the categories and all the blogs associated with each one.

1. You need to associate blogs with your categories, so head to your markdown files and add some categories inside the metadata.   

```markdown  
---  
title: "How to create multi author blog site using Hugo"  
date: 2019-03-20T18:42:38+02:00  
description: "In this tutorial you're going to learn how to create a multi author blogging site in Hugo"  
author: siddhantvarma  
categories : ["Web Development","Web Design","Blogging"]  
---  
```  

Hugo provides taxonomy, which classifies logical relationships between content. According to [Hugo’s documentation](https://gohugo.io/content-management/taxonomies/), it offers default taxonomy support for categories and tags. This means you can easily set up a category taxonomy for your site.

2. Specify that you want to use the category taxonomy inside the `config.toml` file:  

```toml  
[taxonomies]  
  category = "categories"  
```  

3. Inside your `_default` folder, create a file called `taxonomy.html` that ranges through the taxonomies, and then loops through each taxonomy to list out all the items pertaining to that taxonomy name. In this case, each taxonomy is a particular category, and blogs pertaining to each category are listed under that category as that taxonomy's value.  

```html  
{{ define "main" }}  
<section class="section">  
    <div class="container max-800px">  
        <h1 class="title">  
            {{ .Title }}  
        </h1>  
        <div class="categories">  
            {{ range $taxonomyname, $taxonomy := .Site.Taxonomies }}  
                  
                 {{ range $name, $value := $taxonomy }}  
              <div class="categoryCard">  
                 <div class="categoryHeading"><p style="font-size:large">{{ $name }} </p></div>  
                      <div class="category__detail">  
                        {{ range $value.Pages }}  
                            <p hugo-nav="{{ .RelPermalink}}"><a href="{{ .Permalink}}"> {{ .LinkTitle }} </a> </p>  
                        {{ end }}    
                      </div>                  
              </div>  
              {{ end }}  
            {{ end }}  
          </div>  
    </div>  
</section>  
{{ end }}  
```  

4. Apply some minimal styles to your template.   

```css  
.categories{  
  display: flex;  
  justify-content: space-between;  
}  
  
.categoryCard{  
  display: flex;  
  flex-direction: column;  
  width: auto;  
  max-width: 200px;  
  min-height: 200px;  
  margin-right: 5px;  
  height: auto;  
  background-color: #fff;  
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;  
}  
  
.categoryHead{  
  text-align: center;  
  background-color: #f07979;  
  color: #fff;  
  font-weight: bold;  
}  
  
.category__details{  
 padding: 0 10px;  
}  
  
.categoryCard p{  
  font-size: 14px;  
}  
```  

5. Visit `/categories` via the navbar to see your category page. 
[Your blog’s category page](https://imgur.com/d3oCzJ5.png)   

### Considering SEO  
Finally, your theme should be optimized for search engines to ensure your site draws users. Two factors in particular affect SEO for your site:

- The SEO title
- The meta description

Your homepage’s title can be populated from your `config.toml` file. For other pages, a unique title and meta description should be dynamically generated to make these pages easily discoverable by search engines.

Use the following generic code inside your `head.html` file: 

```html  
<head>  
    <meta charset="utf-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">  
    <title>{{ if not .IsHome }}{{ with .Title }}{{ . }} | {{ end }}{{ end }}{{ .Site.Title }}</title>  
    <meta name="description" content="{{ with .Description }}{{ . }}{{ else }}{{ with .Summary }}{{ . }}{{ else }}{{ .Site.Params.description }}{{end }}{{ end }}">  
    <link rel="canonical" href="{{ .Permalink }}" />  
	<link rel="stylesheet" href="/css/style.css" type="text/css" media="all" />  
    {{ template "_internal/opengraph.html" . }}  
    {{ template "_internal/twitter_cards.html" . }}  
</head>  
```  

The previous code checks whether you're at a root route, then fetches the title from the `config.toml` file. For other subroutes, it uses a different title according to the page you're currently on and appends the homepage title to it.

If you inspect each page's `<head>` tag, you'll notice a more specific and relevant title attached to it with an SEO-friendly meta description.   

## Next Steps  
Use the theme you built here as a boilerplate for your own multi-author blog. Customize it even further according to the needs of your brand—extend taxonomies by adding tags and maybe create promotional pages, like an about page or a contact page.  Now that you also understand how custom styling works in Hugo, add some media queries to make your site more responsive.   

Hugo’s functionality simplifies the potentially daunting task of creating a custom theme, while offering you fine-grained control over your branding and the flexibility to accommodate change in the future.
