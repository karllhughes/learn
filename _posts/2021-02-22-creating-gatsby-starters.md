---
layout: post
title: Creating Gatsby Starters
description: Learn how to create your own Gatsby Starter for a blog and why it
  can be a better option than using a ready-made starter
categories: platforms
author: ashutosh
date: 2021-02-23T11:16:13.255Z
img: /assets/posts/jvijan5.png
---
# Creating Gatsby Starters

[GatsbyJS](https://www.gatsbyjs.com/) is an open-source [React](https://reactjs.org/)-based, [GraphQL](https://graphql.org/) powered static site generator. You can create blazingly fast websites in minutes using Gatsby, and many [technical companies use it for their blogs](https://draft.dev/learn/posts/blogging-platforms).

[Gatsby Starters](https://www.gatsbyjs.com/docs/starters/) are boilerplates that you, as a developer, can use to set up a new site with preconfigured tools and plugins instantly. You can modify and build on top of the starters to speed up your development process.

You might ask, why create your own starter? Why not just use an existing starter? There are a few reasons developers invest the time building a starter:

- To help other developers build a better site on Gatsby using unique features or designs.
- To showcase it in the official Gatsby Starter Library and gain recognition for your work.
- To promote your freelance services by creating a portfolio starter with your information. Every time someone uses your starter, they will see your portfolio.

### Tutorial Overview
In this tutorial, I’ll show you how to build a [Gatsby](https://www.gatsbyjs.com/) starter from scratch using [MDX](https://mdxjs.com/) and [Styled Components](https://styled-components.com/), the best CSS-in-JS tool. If you want to jump right into the code, check out the [GitHub Repo here](https://github.com/lelouchB/gatsby-starter-blog), and check out [the deployed version here](https://lelouchb-gatsby-starter-blog.netlify.app/).

More specifically, here’s what I’ll cover in this tutorial:

- [Prerequisites](#prerequisites)
- [Setting Up Gatsby](#setting-up-gatsby)
- [Using Styled Components with Gatsby](#using-styled-components-with-gatsby)
- [Creating a Container Component](#creating-a-container-component)
- [Creating a Bio Component](#creating-a-bio-component)
- [Creating an SEO Component](#creating-an-seo-component)
- [Displaying Posts on Home Page](#displaying-posts-on-the-home-page)
- [Creating Pages from Data](#creating-pages-from-data)
- [Creating a 404 Page](#creating-a-404-page)
- [Adding a Manifest to Your Gatsby Starter](#adding-a-manifest-to-your-gatsby-starter)
- [Adding a Sitemap](#adding-a-sitemap)
- [Adding an RSS Feed](#adding-an-rss-feed)
- [Finishing the Starter](#finishing-the-starter)

## Prerequisites
Before we get started, you should have:

1. Knowledge of [HTML, CSS, and JavaScript](https://www.freecodecamp.org/learn/responsive-web-design/).
2. Basic knowledge of [React](https://reactjs.org/), [Gatsby](https://www.gatsbyjs.com/), and [GraphQL](https://graphql.org/).
3. [Node](https://nodejs.org/en/) and NPM installed on your local dev machine.
4. Any code editor of your choice.
5. [React Dev Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) (optional)

## Setting Up Gatsby

In this tutorial, you will use the Gatsby CLI tool to generate a Gatsby-powered site with minimal configurations quickly.

Run the following command in your terminal to create a Gatsby site with minimal configuration using [Gatsby Hello World Starter](https://github.com/gatsbyjs/gatsby-starter-hello-world).

```bash
gatsby new gatsby-starter-blog https://github.com/gatsbyjs/gatsby-starter-hello-world
cd gatsby-starter-blog
gatsby develop
```
You can read more about setting up your Gatsby development environment [here](https://www.gatsbyjs.com/docs/tutorial/part-zero/).

### `gatsby-source-filesystem` Plugin

The next step is to install the plugins you will use in this starter blog, the first of which is [`gatsby-source-filesystem`](https://www.gatsbyjs.com/plugins/gatsby-source-filesystem/?=gatsby%20source#gatsby-source-filesystem). This plugin creates **File** nodes which point to the location of each file to the GraphQL query gets data from.

You can read more about sourcing from the file system [here](https://www.gatsbyjs.com/docs/how-to/sourcing-data/sourcing-from-the-filesystem/).

Run the following command in your project's root directory.

```bash
npm install gatsby-source-filesystem
```

Now, update the `gatsby-config.js` file to use this plugin.

```jsx
// gatsby-config.js
module.exports = {
  plugins: [
	{
  	resolve: `gatsby-source-filesystem`,
  	options: {
    	name: `pages`,
    	path: `${__dirname}/src/pages`,
  	},
	},
	{
  	resolve: `gatsby-source-filesystem`,
  	options: {
    	name: `posts`,
    	path: `${__dirname}/src/posts`,
  	},
	},
	{
  	resolve: `gatsby-source-filesystem`,
  	options: {
    	name: `images`,
    	path: `${__dirname}/src/images`,
  	},
	},
  ],
};
```

In the above code, you have three instances of the `gatsby-source-filesystem` plugin for `pages`, `posts`, and `images` folder. All the JavaScript files like `index.js` reside in the `pages` directory, `posts` folder is where your articles are stored. The `images` folder is for any images or image resource you might need in your blog like your profile picture.


Now, create the `posts` and `images` folders inside the `src` directory. Run the following commands in the terminal.

```bash
cd src
mkdir posts
mkdir images
cd ..
```

### `gatsby-plugin-google-fonts` Plugin
I like using [Google Fonts](https://fonts.google.com/) as a free improvement over most operating systems’ standard font options. To use Google Fonts in Gatsby, install the [`gatsby-plugin-google-fonts`](https://www.gatsbyjs.com/plugins/gatsby-plugin-google-fonts/?=gatsby%20google%20fonts) plugin.

```bash
npm install gatsby-plugin-google-fonts
```

Update `gatsby-config.js` to use the `gatsby-plugin-google-fonts` plugin.

```jsx
{
  resolve: `gatsby-plugin-google-fonts`,
  options: {
	fonts: ["Satisfy", "Montserrat", "JetBrains Mono"],
	display: "swap"
  }
}
```

Feel free to explore [Google Fonts](https://fonts.google.com/) and import the fonts of your choice.

### `gatsby-plugin-sharp` and `gatsby-transformer-sharp` Plugins

Optimizing images on your blog improves user experience by making response times faster. This in turn can help your blog’s ranking in search engines and makes your site more usable on mobile internet connections, so it’s important to optimize your images.

Run the following command to install the [`gatsby-plugin-sharp`](https://www.gatsbyjs.com/plugins/gatsby-plugin-sharp/) and the [`gatsby-transformer-sharp`](https://www.gatsbyjs.com/plugins/gatsby-transformer-sharp/) plugins that will help optimize the images in your starter.

```bash
npm install gatsby-plugin-sharp gatsby-transformer-sharp
```

### `gatsby-plugin-mdx` Plugin

[MDX](https://mdxjs.com/) is a variant of traditional markdown that lets you write JSX in your markdown files. With MDX you can style and customize your posts in the markdown file itself and can even load dynamic data in them.

Run the following command to install the [`gatsby-plugin-mdx`](https://www.gatsbyjs.com/plugins/gatsby-plugin-mdx/).

```bash
npm install gatsby-plugin-mdx @mdx-js/mdx @mdx-js/react gatsby-remark-images
```

This plugin will allow you to create pages with `.mdx` and `.md` extensions in `src/posts` and process any Gatsby nodes with Markdown media types into MDX content.

Update `gatsby-config.js` to include the `gatsby-plugin-mdx`, `gatsby-plugin-sharp` and `gatsby-transformer-sharp` plugins.

```jsx
// gatsby-config.js
module.exports = {
  plugins: [
	{
  	resolve: `gatsby-source-filesystem`,
  	options: {
    	name: `pages`,
    	path: `${__dirname}/src/pages`,
  	},
	},
	{
  	resolve: `gatsby-source-filesystem`,
  	options: {
    	name: `posts`,
    	path: `${__dirname}/src/posts`,
  	},
	},
	{
  	resolve: `gatsby-source-filesystem`,
  	options: {
    	name: `images`,
    	path: `${__dirname}/src/images`,
  	},
	},
	{
  	resolve: `gatsby-plugin-google-fonts`,
  	options: {
    	fonts: ["Satisfy", "Montserrat", "JetBrains Mono"],
    	display: "swap",
  	},
	},
	`gatsby-plugin-sharp`,
	`gatsby-transformer-sharp`,
	{
  	resolve: `gatsby-plugin-mdx`,
  	options: {
    	extensions: [`.md`, `.mdx`],
    	gatsbyRemarkPlugins: [
      	{
        	resolve: `gatsby-remark-images`,
        	options: {
          	maxWidth: 590,
        	},
      	},
    	],
  	},
	},
  ],
};
```

## Using Styled Components with Gatsby
[Styled Components](https://styled-components.com/docs/basics#getting-started) is an amazing CSS-in-JS tool that lets you write CSS in your JavaScript files. This makes it easy to manage all your styling without having any CSS files in your project.

There are many other benefits and advantages of CSS-in-JS like managing dead code elimination becomes easier with it, styles are scoped to a specific component. It also makes it easier to write unit tests. Many CSS-in-JS libraries also have built-in support for animations, source maps and caching.

Run the following command in the terminal to install the `gatsby-plugin-styled-components` plugin.

```bash
npm install gatsby-plugin-styled-components styled-components babel-plugin-styled-components
```

Update the `gatsby-config.js` file to include this plugin.

```jsx
module.exports = {
  plugins: [
	// other plugins

	`gatsby-plugin-styled-components`,
  ],
};
```

Now create a `global-styles.js` file to add global styles and theme to the app. Global Styles as the name suggests are the styles that are scoped to the global level in your app. For example, if you define the `font-size` property as `3rem` in global styles then the font size of all text will be changed to `3rem` across your app.

A `theme` is an object or set of styles that you can define and access in your CSS-in-JS. For example, if you want to add dark mode to your app, you can define two nested objects in the `theme` object, one for light mode and another for dark mode. Each object will have properties like background color, font color, etc., and when the user clicks the dark mode button, it will toggle between the light and dark styles object.

You can read more about this [here](https://styled-components.com/docs/advanced#theming).

Run the following command in your terminal.

```bash
cd src
mkdir themes
cd themes
touch global-styles.js
```

Add the following code to the `global-styles.js` file.

```jsx
// global-styles.js
import { createGlobalStyle } from "styled-components";

export const theme = {
  colors: {
	primary: "#363537;",
	primaryDark: "#313032",
	primaryDarker: "#2e2d2f",
	primaryDarkest: "#262527",
	primaryLight: "#3b3a3d",
	primaryLighter: "#3e3d3f",
	primaryLightest: "#464548",
  },
  fonts: "Montserrat, Verdana,sans,  serif",
  fontSizes: {
	small: "1em",
	medium: "1.5em",
	large: "2em",
  },
};

export const GlobalStyles = createGlobalStyle`
*, *:before, *:after {
	box-sizing: border-box;
	margin:0;
	padding:0;
  }

  html {
	scroll-behavior: smooth;
	font-family: ${(props) => props.theme.fonts};
	background-color:#f7f7f7;
	font-size: ${(props) => props.theme.fontSizes.medium};
	padding: 0 1rem;
  }

  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
	color: ${(props) => props.theme.colors.primaryDarkest};
	margin: 1rem 0;
  }
  h1 {
	font-size: 1.95rem;
	line-height: 2rem;
	font-weight: 400;
  }
  h2 {
	font-size: 1.5rem;
	line-height: 1.75rem;
	font-weight: 400;
  }
  h3 {
	font-size: 1.35rem;
	line-height: 1.625rem;
	font-weight: 400;
  }
  h4 {
	font-size: 1.15rem;
	line-height: 1.5rem;
	font-weight: 400;
  }

  h5 {
	font-size: 1.095rem;
	line-height: 1.375rem;
	font-weight: 700;
  }

  h6 {
	font-size: 1rem;
	line-height: 1.5rem;
	font-weight: 700;
  }
 `;
```

In the above code, you created a `theme` object with some basic CSS and used the `createGlobalStyle` function from `styled-components` to add global styles to the app.

To use the theme and global styles, you need to create a file named `gatsby-browser.js` in the project's root directory. Run the following command in your project's root directory.

```bash
touch gatsby-browser.js
```

Add the following code to the `gatsby-browser.js` file.

```jsx
// gatsby-browser.js
import React from "react";
import { GlobalStyles, theme } from "./src/themes/global-styles";
import { ThemeProvider } from "styled-components";

export const wrapRootElement = ({ element }) => (
  <ThemeProvider theme={theme}>
	<GlobalStyles />
	{element}
  </ThemeProvider>
);
```

Here you use the [`wrapRootElement`](https://www.gatsbyjs.com/docs/browser-apis/#wrapRootElement) function from `gatsby` to wrap the entire root element with `ThemeProvider` wrapper component from `styled-components`, which provides a theme to all React components underneath itself via the context API.

You pass the `theme` object created in the `global-styles.js` file to the `theme` prop of the `ThemeProvider` component.

Then you pass the `GlobalStyles` component at the top of the React tree.

You can access the `theme` object attributes as props in any of the component like `${props => props.theme.fontSizes.medium};`.

Start your development server by running the `gatsby develop` command and head over to [http://localhost:8000/](http://localhost:8000/).

![Global Styles](https://i.imgur.com/9mjNQVj.png)

You will notice that the background-color, font, etc., of the app, has changed according to the CSS in the `GlobalStyles` component.

## Creating a Container Component

Your Starter should have consistent styling and a common layout throughout the different pages or it will seem messy and result in bad user experience. In this section, you will create a `Container` component that will wrap your entire app with a navbar and a footer. The `Container` component is the common layout of your starter and contains other components such as a `Footer` component and a `Navbar` component.

Although it's not a requirement for a Gatsby Starter to have such a `Container` component, you will find that by splitting code into different components, it becomes easier to manage and helps remove repeated code. For example, every page in your starter will have a footer, so instead of repeating the same code, make and use a separate `Footer` component in its place.

In the `src` directory, create a file named `Container.js` inside a folder named `components` by running the following command.

```bash
cd src
mkdir components
cd components
touch Container.js
```

Add the following code to `Container.js`.

```jsx
// Container.js
import React from "react";
import styled from "styled-components";

const ContainerWrapper = styled.div`
  height: 100%;
  display: block;
  margin: auto;
  max-width: 640px;
`;
export const Container = ({ children }) => {
  return <ContainerWrapper>{children}</ContainerWrapper>;
};
```

This `Container` component defines the layout of your app.

Update the `pages/index.js` file to include the `Container` component like this.

```jsx
// index.js
import React from "react";
import { Container } from "../components/Container";

export default function Home() {
  return <Container>Hello world!</Container>;
}
```

With your development server still running, navigate to [http://localhost:8000/](http://localhost:8000/) to see your app with the new container.

![Container Component](https://i.imgur.com/6uepw9Z.png)

### Creating a Navbar Component

The next step is to create a navbar component and use it inside the `Container` component.

Run the following command inside the `components` directory to create the `Nav.js` file.

```bash
touch Nav.js
```

You will also need to install `react-icons` to add icons to your blog. This package includes some of the most popular icon libraries like Ant Design Icons, Bootstrap Icons, and more. Having different icons in your Starter can result in better user experience, and social media icons (Instagram, LinkedIn, Facebook) can help your readers connect with you on different platforms.

Install `react-icons` by running the following command.

```bash
npm install react-icons
```

Add the following code to `Nav.js`.

```jsx
// Nav.js
import React from "react";
import { Link } from "gatsby";
import { FaRegMoon } from "react-icons/fa";
import styled from "styled-components";

const NavWrapper = styled.nav`
  font-size: 1.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: row;
  margin-top: 0.3rem 0.6rem;

  a {
	text-decoration: none;
	font-family: Satisfy;
	color: #6a5acd;
  }
  svg {
	font-size: 1rem;
	color: #4a4656;
	&:hover {
  	color: #000;
	}
  }
  @media only screen and (max-width: 480px) {
	font-size: 1rem;
  }
`;
export const Nav = () => {
  return (
	<NavWrapper>
  	{/* Replace with your Name */}
  	<Link to="/">Ashutosh K Singh</Link>
  	<FaRegMoon />
	</NavWrapper>
  );
};
```

In the above code, you use the [`Link`](https://www.gatsbyjs.com/docs/gatsby-link/) component to add a link to the homepage, i.e., to the `/` page. Make sure to replace the text inside the `Link` component with your name. You can also use a logo instead of text.

Update the `Container.js` file to include this component like this.

```jsx
// Container.js
import React from "react"
import styled from "styled-components"
import { Nav } from "./Nav"

const ContainerWrapper = styled.div`
  height: 100%;
  display: block;
  margin: auto;
  max-width: 640px;
`
export const Container = ({ children }) => {
  return (
	<ContainerWrapper>
  	{" "}
  	<Nav />
  	{children}
	</ContainerWrapper>
  )
}
```

Head over to [http://localhost:8000/](http://localhost:8000/) to see your app with the new navbar component and icon.

![Navbar in Container](https://i.imgur.com/S5RJYvo.png)

### Creating a Footer Component

The next step is to create a `Footer.js` file to add a footer to the `Container` component. Run the following command inside the `components` directory to create the `Footer.js` file.

```bash
touch Footer.js
```

Add the following code to the `Footer.js` file.

```jsx
import React from "react";
import {
  FaRegEnvelope,
  FaGithub,
  FaLinkedinIn,
  FaTwitter,
  FaFacebookF,
  FaInstagram,
  FaRss,
} from "react-icons/fa";
import styled from "styled-components";

const FooterWrapper = styled.footer`
  min-height: 12rem;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 3rem 0;
  margin-bottom: 2rem;

  p {
	font-size: 0.8rem;
	font-weight: 300;
  }
  ul {
	text-align: center;
	li {
  	display: inline-block;
  	a {
    	svg {
      	color: #4a4656;
      	&:hover {
        	color: #8a2be2;
      	}
    	}
  	}
	}
	li:not(:last-child) {
  	margin-right: 40px;
	}
  }
`;
export const Footer = () => {
  const config = {
	email: `admin@ashusingh.me`,
	githubUsername: `lelouchB`,
	twitterUsername: `noharashutosh`,
	instagramUsername: `singhashutoshk`,
	siteUrl: `http://localhost:8000/`,
  };
  const linkedinUrl = `https://www.linkedin.com/in/ashutosh-singh-550a6a178`;
  const instagramUrl = `https://www.instagram.com/${config.instagramUsername}`;
  const mailToUrl = `mailto:${config.email}?Subject=Hello`;
  const twitterUrl = `https://twitter.com/${config.twitterUsername}`;
  const facebookURL = `https://facebook.com/`;
  const githubUrl = `https://github.com/${config.githubUsername}`;
  const rssFeed = `${config.siteUrl}/rss.xml`;

  return (
	<FooterWrapper>
  	<ul>
    	<li>
      	<a href={mailToUrl} target="_top" title="Email">
        	<FaRegEnvelope />
      	</a>
    	</li>

    	<li>
      	<a
        	href={githubUrl}
        	target="_blank"
        	title="Contact Ashutosh at GitHub"
        	rel="noopener noreferrer"
      	>
        	<FaGithub />
      	</a>
    	</li>
    	<li>
      	<a
        	href={linkedinUrl}
        	target="_blank"
        	title="Contact Ashutosh on Linkedin"
        	rel="noopener noreferrer"
      	>
        	<FaLinkedinIn />
      	</a>
    	</li>
    	<li>
      	<a
        	href={twitterUrl}
        	target="_blank"
        	title="Contact Ashutosh on Twitter"
        	rel="noopener noreferrer"
      	>
        	<FaTwitter />
      	</a>
    	</li>
    	<li>
      	<a
        	href={facebookURL}
        	target="_blank"
        	title="Contact Ashutosh on Facebook"
        	rel="noopener noreferrer"
      	>
        	<FaFacebookF />
      	</a>
    	</li>

    	<li>
      	<a
        	href={instagramUrl}
        	target="_blank"
        	title="Contact Ashutosh on Instagram"
        	rel="noopener noreferrer"
      	>
        	<FaInstagram />
      	</a>
    	</li>
    	<li>
      	<a
        	href={rssFeed}
        	target="_blank"
        	title="RSS Feed"
        	rel="noopener noreferrer"
      	>
        	<FaRss />
      	</a>
    	</li>
  	</ul>
  	<p>
    	Handcrafted with{" "}
    	<span role="img" aria-label="white_heart">
      	🤍
    	</span>{" "}
    	by me
  	</p>
	</FooterWrapper>
  );
};
```

The code above first imports all the different icons from `react-icons` and then creates an unordered list with all the icons. Inside the `<li>` tag, it uses `<a>`s to add different social links like Facebook, Instagram, etc.

One thing you may notice is the `rssFeed`, which points to [http://localhost:8000/rss.xml](http://localhost:8000/rss.xml). You can ignore this for now, but this is the route where you will create the RSS feed for your blog later in this tutorial.

Remember to replace the above links with your social handles and URLs.

Update the `Container.js` file to include this `Footer` component like this.

```jsx
// Container.js
import React from "react";
import styled from "styled-components";
import { Nav } from "./Nav";
import { Footer } from "./Footer";

const ContainerWrapper = styled.div`
  height: 100%;
  display: block;
  margin: auto;
  max-width: 640px;
`;
export const Container = ({ children }) => {
  return (
	<ContainerWrapper>
  	<Nav />
  	{children}
  	<Footer />
	</ContainerWrapper>
  );
};
```

Head over to [http://localhost:8000/](http://localhost:8000/). Here is how your app will look now.

![Footer in Container](https://i.imgur.com/18OgrJD.png)

## Creating a Bio Component

In this section, you will create a `Bio` component with an image and some information about the author. Having a bio will help readers connect with you on a more personal level. You can tell them about yourself, why you write articles, and where they can find your other work. A good bio section helps build a sense of trust between content creators like bloggers and the readers.

In this section, I’ll refer to an image named `myAvatar.png` inside the `src/images` directory. You can either replace this with your avatar or download the image used in this tutorial from [here](https://github.com/lelouchB/gatsby-starter-blog/raw/main/src/images/myAvatar.png).

As you may remember, you installed [`gatsby-plugin-sharp`](https://www.gatsbyjs.com/plugins/gatsby-plugin-sharp/) and [`gatsby-transformer-sharp`](https://www.gatsbyjs.com/plugins/gatsby-transformer-sharp/) plugins in the above sections to optimize your images. Now you need to install the `gatsby-image` component to make use of those plugins.

Run the following command in your project's root directory to install `gatsby-image`.

```bash
npm install gatsby-image
```

Run the following command inside the `components` folder to create a `Bio.js` file.

```bash
touch Bio.js
```

Add the following code to `Bio.js`.

```jsx
// Bio.js
import React from "react";
import styled from "styled-components";
import Img from "gatsby-image";
import { useStaticQuery, graphql } from "gatsby";
import { GiDove } from "react-icons/gi";

const BioWrapper = styled.div`
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  margin-top: 0.4rem;
  svg {
	color: purple;
	font-size: 2rem;
  }
  h2 {
	margin-bottom: 0.5rem;
  }
  h3 {
	margin: 0.8rem 0;
	font-weight: 600;
  }
`;
export const Bio = () => {
  const data = useStaticQuery(graphql`
	query {
  	imageSharp(fixed: { originalName: { eq: "myAvatar.png" } }) {
    	id
    	fixed(width: 250, height: 250) {
      	...GatsbyImageSharpFixed
    	}
  	}
	}
  `);
  return (
	<BioWrapper>
  	<Img
    	fixed={data.imageSharp.fixed}
    	style={{ borderRadius: "50%", left: "0", top: "0" }}
    	alt="My Avatar"
  	/>
  	<h2>
    	Hey Stranger <GiDove />
  	</h2>

  	<br />
  	<p>
    	My name is <b>Ashutosh</b>! I'm a JavaScript Developer & Technical
    	Writer. I develop awesome stuff with JavaScript and love to write about
    	them.
  	</p>
  	<h3>Latest Posts</h3>
	</BioWrapper>
  );
};
```

In the above code, you added a `Hey Stranger` message and a short bio. Make sure to update these paragraphs with your information.

Take a look at how you are fetching the `myAvatar.png` image.

```bash
 const data = useStaticQuery(graphql`
	query {
  	imageSharp(fixed: { originalName: { eq: "myAvatar.png" } }) {
    	id
    	fixed(width: 250, height: 250) {
      	...GatsbyImageSharpFixed
    	}
  	}
	}
  `)
```

Here you are using the [`useStaticQuery`](https://www.gatsbyjs.com/docs/use-static-query/) hook and `graphql` imported from `gatsby`. `useStaticQuery` hook does not accept variables (hence the name “static”), and is used here to find with `originalName: { eq: "myAvatar.png" }`. Replace `myAvatar.png` with your image name. You can read more about `...GatsbyImageSharpFixed` [here](https://www.gatsbyjs.com/docs/reference/built-in-components/gatsby-image/#image-query-fragments).

You then pass this `data.imageSharp.fixed` to the `Img` component from `gatsby-image` like this.

```jsx
<Img
  fixed={data.imageSharp.fixed}
  style={{ borderRadius: "50%", left: "0", top: "0" }}
  alt="Avatar"
/>
```

Update the `pages/index.js` file to include this `Bio` component.

```jsx
// index.js
import React from "react";
import { Container } from "../components/Container";
import { Bio } from "../components/Bio";

export default function Home() {
  return (
	<Container>
  	<Bio />
	</Container>
  );
}
```

Restart your development server and head over to [http://localhost:8000/](http://localhost:8000/) to see the bio component on your blog’s home page:

![Bio Component](https://i.imgur.com/1wDxrKC.png)

## Creating an SEO Component
SEO stands for **Search Engine Optimization**, it means that you are optimizing your website to rank better in the results on search engines like Google. There are many factors that affect your site rank on Google or other search engines like the [web crawl accessibility](https://developer.mozilla.org/en-US/docs/Glossary/Crawler),  optimized keywords on each page, fast loading speeds, good user experience, and more. 

Gatsby can help your site rank and perform better in search engines. Because Gatsby pages are server-rendered, the crawlers are easily able to access your site. You can also add meta information so the search engines can understand your content and know where to show your pages in search results.  You can read more about SEO for Gatsby [here](https://www.gatsbyjs.com/docs/seo/).

In this section, you will create an `SEO` component that adds basic meta-tags like the `title`, `description`, or `lang`, etc., of the page in the `<head>` element.

Run the following command to install the `gatsby-plugin-react-helmet` plugin and the `react-helmet` library.

```bash
npm install gatsby-plugin-react-helmet react-helmet
```

Stop your development server and update the `gatsby-config.js`. Make sure to update the fields with your social handles and information.

```jsx
// gatsby-config.js
module.exports = {
  siteMetadata: {
	title: `Gatsby Starter Blog`,
	author: {
  	name: `Ashutosh Kumar Singh`,
	},
	description: `Gatsby Starter Blog built with MDX and Styled Components.`,
	image: `/cover.png`,
	siteUrl: `https://lelouchb-gatsby-starter-blog-demo.netlify.app/`,
	social: {
  	twitter: `@noharashutosh`,
	},
  },
  plugins: [
	// plugins
	`gatsby-plugin-react-helmet`,
  ],
};
```

One thing that you might notice is the `cover.png` image in the `image` field. This image will be used in the social card preview of the site. This image is stored inside the `static` directory. You can either use a customized image or download the cover image used in this tutorial from [here](https://github.com/lelouchB/gatsby-starter-blog/raw/main/static/cover.png).

Head over to [localhost:8000/\_\_graphql](http://localhost:8000/__graphql) and paste the following query in the left tab.

```graphql
{
  site {
	siteMetadata {
  	title
  	description
  	social {
    	twitter
  	}
  	author {
    	name
  	}
  	image
  	siteUrl
	}
  }
}
```

Hit the run button. You will see an output similar to this.

```json
{
  "data": {
	"site": {
  	"siteMetadata": {
    	"title": "Gatsby Starter Blog",
    	"description": "Gatsby Starter Blog built with MDX and Styled Components.",
    	"social": {
      	"twitter": "@noharashutosh"
    	},
    	"author": {
      	"name": "Ashutosh Kumar Singh"
    	},
    	"image": "/cover.png",
    	"siteUrl": "https://lelouchb-gatsby-starter-blog.netlify.app"
  	}
	}
  },
  "extensions": {}
}
```

This is the query that you will use with the `useStaticQuery` hook in the `Seo.js` file.

Create a file named `Seo.js` under the `components` directory.

```bash
cd components
touch Seo.js
```

Add the following code to the `Seo.js` file.

```jsx
// Seo.js
import React from "react";
import PropTypes from "prop-types";
import { Helmet } from "react-helmet";
import { useStaticQuery, graphql } from "gatsby";

export const SEO = ({ title, lang, meta, description }) => {
  const { site } = useStaticQuery(
	graphql`
  	query {
    	site {
      	siteMetadata {
        	title
        	description
        	social {
          	twitter
        	}
        	author {
          	name
        	}
        	image
        	siteUrl
      	}
    	}
  	}
	`
  );

  const metaDescription = description || site.siteMetadata.description;
  const defaultTitle = site.siteMetadata?.title;
  const siteUrl = site.siteMetadata?.siteUrl;
  const image = site.siteMetadata?.image;

  return (
	<Helmet
  	htmlAttributes={{
    	lang,
  	}}
  	title={title}
  	titleTemplate={defaultTitle ? `%s | ${defaultTitle}` : null}
  	meta={[
    	{
      	name: `title`,
      	content: title,
    	},
    	{
      	name: `description`,
      	content: metaDescription,
    	},
    	{
      	property: `og:title`,
      	content: title,
    	},
    	{
      	property: `og:description`,
      	content: metaDescription,
    	},
    	{ property: "og:locale", content: lang },
    	{
      	property: "og:site_name",
      	content: "Gatsby Starter Blog",
    	},
    	{
      	property: `og:type`,
      	content: `website`,
    	},
    	{
      	property: `og:image`,
      	content: `${siteUrl}${image}`,
    	},
    	{
      	name: `twitter:card`,
      	content: `summary_large_image`,
    	},
    	{
      	name: `twitter:creator`,
      	content: site.siteMetadata?.social?.twitter || ``,
    	},
    	{
      	name: `twitter:title`,
      	content: title,
    	},
    	{
      	name: `twitter:description`,
      	content: metaDescription,
    	},
    	{
      	name: `twitter:image`,
      	content: `${siteUrl}${image}`,
    	},
  	].concat(meta)}
	/>
  );
};

SEO.defaultProps = {
  lang: `en`,
  meta: [],
  description: ``,
};

SEO.propTypes = {
  description: PropTypes.string,
  lang: PropTypes.string,
  meta: PropTypes.arrayOf(PropTypes.object),
  title: PropTypes.string.isRequired,
};
```

You will not notice any change in the app since you have created the `SEO` component, but have not used it in any of the pages yet. You’ll see how to incorporate your `SEO` component in the next section.

## Displaying Posts on Home Page

In this section, you will create dummy posts for the starter blog, query them in the `pages/index.js` file, and show them on the homepage.

For this tutorial, I chose to create a separate folder for each post. This folder includes the `markdown` file and the accompanying images, videos, etc. This is not strictly necessary, but having a single folder for all posts can become a little hard to manage as your blog scales and you have more images and media assets to incorporate.

Inside the `src/posts` directory, create a folder named `my-first-post` and inside it create a file named `index.mdx`. Add sample data to `index.mdx` from [here](https://raw.githubusercontent.com/lelouchB/gatsby-starter-blog/main/src/posts/my-first-post/index.mdx).

The content inside `---` is the frontmatter of the post and includes `title`, `slug`, `date`, `tags`, and `excerpt` of the post. You can also include other fields like `keywords`, `cover_image`, `author`, etc., in the frontmatter. You can refer to [Gatsby documentation](https://www.gatsbyjs.com/docs/mdx/writing-pages/#using-frontmatter-in-mdx) for the GraphQL query to fetch data from this post.

But first, you need to create a `PostContainer` component that will take all the fetched data as props and show them in a more styled manner. Run the following code to create a `PostContainer` component under the `components` directory.

```bash
cd src
cd components
touch PostContainer.js
```

Add the following code to the `PostContainer.js` file.

```jsx
import React from "react";
import styled from "styled-components";
import { Link } from "gatsby";

const PostContainerWrapper = styled.div`
  margin-top: 1rem;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #fafafa;
  box-shadow: 2px 3px 4px 6px #ccc;
  border-radius:10px;
  text-align: center;

  h2 {
	font-size: 1.6rem;
	margin: 0.75rem 0;
	font-weight: 500;
	color: {$props=>props.theme.colors.primaryDarkest};
  }
  p {
	font-size: 0.8rem;
  }
  span {
	font-size: 0.75rem;
	margin: 0.2rem 0;
	font-weight: 400;
	color: #949494;
  }
`;

const ButtonWrapper = styled((props) => <Link {...props} />)`
  padding: 0.45rem 0.5rem;
  margin-top: 0.4rem;
  font-size: 0.9rem;
  background-color: #6a5acd;
  border-radius: 0.5rem;
  font-weight: 600;
  color: white;
  text-decoration: none;
`;

export const PostContainer = ({ title, date, excerpt, slug }) => {
  return (
	<PostContainerWrapper>
  	<h2>{title}</h2>
  	<span>{date}</span>
  	<p>{excerpt}</p>
  	<ButtonWrapper to={`posts/${slug}`}>Read More</ButtonWrapper>
	</PostContainerWrapper>
  );
};
```

In the above code, you passed `title`, `date`, `excerpt`, `slug` to the `PostContainer` component as props. You will notice that the`Read More` link does not work since you have not yet created the dynamic route it points to.

Update the `index.js` file to show the posts.

```jsx
import React from "react";
import { graphql } from "gatsby";
import { Container } from "../components/Container";
import { SEO } from "../components/Seo";
import { PostContainer } from "../components/PostContainer";
import { Bio } from "../components/Bio";

export default function Home({ data }) {
  const posts = data.allMdx.edges;
  if (posts.length === 0) {
	return (
  	<Container>
    	<SEO title="All posts" />
    	<Bio />
    	<p>
      	No blog posts found. Add markdown posts to "src/posts" (or the
      	directory you specified for the "gatsby-source-filesystem" plugin in
      	gatsby-config.js).
    	</p>
  	</Container>
	);
  }
  return (
	<Container>
  	<SEO title="Gatsby Starter Blog" />
  	<Bio />

  	{posts.map((post) => (
    	<PostContainer
      	key={post.node.id}
      	date={post.node.frontmatter.date}
      	title={post.node.frontmatter.title}
      	slug={post.node.frontmatter.slug}
      	excerpt={post.node.frontmatter.excerpt}
    	/>
  	))}
	</Container>
  );
}

export const pageQuery = graphql`
  query AllPostsQuery {
	allMdx(sort: { fields: frontmatter___date, order: DESC }) {
  	edges {
    	node {
      	frontmatter {
        	slug
        	title
        	excerpt
        	date(formatString: "MMMM DD, YYYY")
      	}
      	id
    	}
  	}
	}
  }
`;
```

The above code uses the GraphQL query discussed above to fetch posts data and pass them in the `Home` component as `data` prop. Then it checks if there are any posts present using an `if` statement and `posts.length === 0`. If `posts.length > 0` then you use the `.map()` method on the `posts` array and pass the data to the `PostContainer` component.

Navigate to [http://localhost:8000/](http://localhost:8000/) in the browser to see a snippet of your first post on the homepage.

![Homepage with one post](https://i.imgur.com/DORfOeN.png)

Create another post inside the `posts` directory using your command line.

```bash
cd src
cd posts
mkdir markdown-syntax-guide
cd markdown-syntax-guide
touch index.mdx
```

Copy the code from [GitHub](https://github.com/lelouchB/gatsby-starter-blog/tree/main/src/posts/markdown-syntax-guide) to create another post named `markdown-syntax-guide`.

The above markdown file uses an image named `mac.jpg` stored inside the `markdown-syntax-guide` folder. You can download this image from [here](https://github.com/lelouchB/gatsby-starter-blog/raw/main/src/posts/markdown-syntax-guide/mac.jpg).

After saving this markdown file, the homepage will automatically update to show this post.

![Homepage with two posts](https://i.imgur.com/jvijaN5.png)

## Creating Pages from Data

Next, you will create individual pages for each of your posts.

Stop your development server and run the following command to create a `gatsby-node.js` file inside your project's root directory.

```bash
touch gatsby-node.js
```

This file is used to create pages dynamically, add nodes in GraphQL, or respond to events during the build lifecycle. You can read more about it here.

Add the following code in `gatsby-node.js`.

```jsx
// gatsby-node.js
const path = require(`path`);

exports.createPages = async function ({ actions, graphql }) {
  const { createPage } = actions;
  const { data } = await graphql(`
	{
  	allMdx(sort: { fields: frontmatter___date, order: DESC }) {
    	edges {
      	node {
        	frontmatter {
          	slug
        	}
        	id
      	}
    	}
  	}
	}
  `);

  data.allMdx.edges.forEach((post) => {
	const slug = post.node.frontmatter.slug;

	createPage({
  	path: `posts/${slug}`,
  	component: path.resolve(`./src/templates/blog-post.js`),
  	context: { id: post.node.id },
	});
  });
};
```

The above code uses a template file named `blog-post.js` inside the `src/templates` directory to create the posts' page.

Run the following command to create the template `blog-post.js` file.

```bash
cd src
mkdir templates
cd templates
touch blog-post.js
```

Add the following code to `blog-post.js`.

```jsx
// blog-post.js
import React from "react";
import { graphql } from "gatsby";
import { MDXRenderer } from "gatsby-plugin-mdx";
import { Container } from "../components/Container";
import { SEO } from "../components/Seo";
import styled from "styled-components";

const PostWrapper = styled.div`
  padding: 1rem;
  span {
	font-weight: 500;
  }

  p {
	font-size: 1.125 rem;
	font-weight: 400;
	color: #2e2d2f;
	margin: 0.625rem 0;
  }

  a {
	color: blue;
	text-decoration: underline;
  }
  strong {
	font-weight: 700;
  }
  em: {
	font-style: italic;
  }
  del {
	text-decoration: line-through;
  }
  blockquote p {
	font-style: italic;
	font-size: 1.125rem;
	line-height: 1.75rem;
	text-align: center;
	max-width: 36rem;
	margin: 3rem auto;
  }
  ul,
  ol {
	color: #2e2d2f;
	margin: 1rem 0 1rem 2rem;
  }

  li {
	margin: 0.25rem 0;
  }

  table {
	width: 100%;
	border-spacing: 0.25rem;
	border-collapse: collapse;
	font-size: 1rem;
  }
  table,
  th,
  td {
	border: 1px solid #000;
  }
  th {
	font-weight: 700;
  }
  td {
	padding: 0.15rem;
	text-align: left;
  }
`;

const TitleWrapper = styled.div`
  text-align: left;
  font-size: 2.1rem;
  font-family: JetBrains Mono;
  font-weight: 500;
  background: #0f2027;
  background: -webkit-linear-gradient(to right, #2c5364, #203a43, #0f2027);
  background: linear-gradient(to right, #2c5364, #203a43, #0f2027);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
`;

const Title = ({ title }) => {
  return <TitleWrapper>{title}</TitleWrapper>;
};

const DateWrapper = styled.span`
  text-align: left;
  font-size: 0.6rem;
  font-weight: 500;
`;

const Date = ({ date }) => {
  return <DateWrapper>{date}</DateWrapper>;
};
const TimeToReadWrapper = styled.span`
  text-align: left;
  margin-left: 1rem;
  font-size: 0.6rem;
  font-weight: 500;
`;

const TimeToRead = ({ timeToRead }) => {
  return (
	<TimeToReadWrapper>
  	{timeToRead} {timeToRead > 1 ? `MINUTES` : `MINUTE`} TO READ
	</TimeToReadWrapper>
  );
};

const TagsWrapper = styled.div`
  display: flex;
  flex-direction: row;
  max-width: 480px;
  font-size: 0.6rem;
  font-weight: 600;
  color: #ff0099;
`;
const TagWrapper = styled.span`
  padding-right: 0.3rem;
  cursor: pointer;
`;

const Tags = ({ tags }) => {
  return (
	<TagsWrapper>
  	{tags.map((tag) => (
    	<TagWrapper key={tag}>{tag}</TagWrapper>
  	))}
	</TagsWrapper>
  );
};

const singlePost = ({ data }) => {
  return (
	<Container>
  	<SEO
    	title={data.mdx.frontmatter.title}
    	description={data.mdx.frontmatter.excerpt}
  	/>
  	<Title title={data.mdx.frontmatter.title} />
  	<Date date={data.mdx.frontmatter.date} />
  	<TimeToRead timeToRead={data.mdx.timeToRead} />
  	<Tags tags={data.mdx.frontmatter.tags} />
  	<PostWrapper>
    	<MDXRenderer>{data.mdx.body}</MDXRenderer>
  	</PostWrapper>
	</Container>
  );
};

export default singlePost;

export const pageQuery = graphql`
  query SinglePostQuery($id: String!) {
	mdx(id: { eq: $id }) {
  	body
  	frontmatter {
    	date(formatString: "MMMM DD, YYYY")
    	excerpt
    	slug
    	title
    	tags
  	}
  	timeToRead
	}
  }
`;
```

Restart your development server and head over to [http://localhost:8000/](http://localhost:8000/) and click on **Read More** on any post.

Alternatively, head over to [http://localhost:8000/posts/markdown-syntax-guide](http://localhost:8000/posts/markdown-syntax-guide) for the post titled **Markdown Syntax Guide**.

![Markdown Syntax Guide post](https://i.imgur.com/4aMUEQB.png)

## Creating a 404 Page

A 404 page is the page that users see when they try to visit a non-existing URL on your website or when the server cannot find the requested URL. A good 404 page contributes to a better user experience by reducing bounce rate and maintains consistent branding and layout throughout the website.

It can show users that the URL they are trying to access doesn’t exist and redirect them somewhere else (like the home page), or it can show a few popular blog posts to help visitors find something else they might like. Gatsby comes with a prebuilt 404 page for non-existing routes, but it’s probably a good idea to add a custom 404 page to your blog.

Run the following command to create `404.js` inside the `src/pages` directory.

```bash
cd src/pages
touch 404.js
```

Add the following code to the `404.js` file.

```jsx
// 404.js
import React from "react";
import { Container } from "../components/Container";
import { SEO } from "../components/Seo";

const NotFound = () => {
  return (
	<Container>
  	<SEO title="404 Not Found" />
  	<h1>NOT FOUND</h1>
  	<p>You just hit a route that doesn&#39;t exist...</p>
	</Container>
  );
};

export default NotFound;
```

The above code uses the `Container` component to create a 404 page with a simple text that this route doesn't exist. Head over to [http://localhost:8000/404/](http://localhost:8000/404/) to see your new 404 page in action.

![404 Not Found](https://i.imgur.com/pRHfFuS.png)

## Adding a Manifest to Your Gatsby Starter

A Progressive Web Application enhances user experience based on the browser capabilities, makes your website installable as an app on mobile devices, supports caching and offline usage. A PWA also  adds support for push notifications and has access to multiple native APIs such as camera, geo location, payments, etc. 

Gatsby’s manifest plugin configures Gatsby to create a `manifest.webmanifest` file on every site build. Run the following command to install the [`gatsby-plugin-manifest`](https://www.gatsbyjs.com/plugins/gatsby-plugin-manifest/) plugin.

```bash
npm install gatsby-plugin-manifest
```

Stop your development server and update the `gatsby-config.js` file to include the `gatsby-plugin-manifest` plugin like this.

```jsx
{
  resolve: `gatsby-plugin-manifest`,
  options: {
	name: `Gatsby Starter Blog`,
	short_name: `Gatsby`,
	start_url: `/`,
	lang: `en`,
	background_color: `#f7f0eb`,
	theme_color: `purple`,
	display: `standalone`,
	icon: `src/images/myAvatar.png`,
	icon_options: {
      	purpose: `any maskable`,
    	},
  },
},
```

Make sure to update the above fields with your blog data and color scheme. `myAvatar.png` is an image inside the `src/images` folder, so you can replace this with a photo of your choice. 

Restart your development server by running the `gatsby develop` command in the terminal. Head over to [http://localhost:8000/manifest.webmanifest](http://localhost:8000/manifest.webmanifest) where you will see a manifest file like this.

```json
{
  "name": "Gatsby Starter Blog",
  "short_name": "Gatsby",
  "start_url": "/",
  "lang": "en",
  "background_color": "#f7f0eb",
  "theme_color": "purple",
  "display": "standalone",
  "cacheDigest": "d6541ebfd3ce17cfc7741d27bb585271",
  "icons": [
	{
  	"purpose": "any maskable",
  	"src": "icons/icon-48x48.png?v=d6541ebfd3ce17cfc7741d27bb585271",
  	"sizes": "48x48",
  	"type": "image/png"
	},
	{
  	"purpose": "any maskable",
  	"src": "icons/icon-72x72.png?v=d6541ebfd3ce17cfc7741d27bb585271",
  	"sizes": "72x72",
  	"type": "image/png"
	},
	{
  	"purpose": "any maskable",
  	"src": "icons/icon-96x96.png?v=d6541ebfd3ce17cfc7741d27bb585271",
  	"sizes": "96x96",
  	"type": "image/png"
	},
	{
  	"purpose": "any maskable",
  	"src": "icons/icon-144x144.png?v=d6541ebfd3ce17cfc7741d27bb585271",
  	"sizes": "144x144",
  	"type": "image/png"
	},
	{
  	"purpose": "any maskable",
  	"src": "icons/icon-192x192.png?v=d6541ebfd3ce17cfc7741d27bb585271",
  	"sizes": "192x192",
  	"type": "image/png"
	},
	{
  	"purpose": "any maskable",
  	"src": "icons/icon-256x256.png?v=d6541ebfd3ce17cfc7741d27bb585271",
  	"sizes": "256x256",
  	"type": "image/png"
	},
	{
  	"purpose": "any maskable",
  	"src": "icons/icon-384x384.png?v=d6541ebfd3ce17cfc7741d27bb585271",
  	"sizes": "384x384",
  	"type": "image/png"
	},
	{
  	"purpose": "any maskable",
  	"src": "icons/icon-512x512.png?v=d6541ebfd3ce17cfc7741d27bb585271",
  	"sizes": "512x512",
  	"type": "image/png"
	}
  ]
}
```

Now your Gatsby starter will function as a progressive web app, and users will be able to save it to their device’s home screen. You can also enable offline mode, push notifications, or [any of the other features PWAs offer](https://www.altexsoft.com/blog/engineering/progressive-web-apps/).

## Adding a Sitemap

A sitemap is an XML file that lists a website’s essential pages, making sure search engines (such as Google) can find and crawl them all. In this section, I’ll show you how to add a sitemap to your Gatsby starter.

Stop your development server and install the `gatsby-plugin-sitemap` plugin by running the following command.

```bash
npm install gatsby-plugin-sitemap
```

Update `gatsby-config.js` to include this `gatsby-plugin-sitemap` plugin.

```jsx
// gatsby-config.js
module.exports = {
  siteMetadata: {
	// siteMetadata
  },
  plugins: [
	// plugins
	{
  	resolve: `gatsby-plugin-sitemap`,
  	options: {
    	output: `/sitemap.xml`,
    	query: `
        	{
          	site {
            	siteMetadata {
              	siteUrl
            	}
          	}
         	 
          	allSitePage {
            	nodes {
              	path
            	}
          	}
      	}
      	`,
    	resolveSiteUrl: ({ site, allSitePage }) => {
      	return site.siteMetadata.siteUrl;
    	},
    	serialize: ({ site, allSitePage }) =>
      	allSitePage.nodes.map((node) => {
        	return {
          	url: `${site.siteMetadata.siteUrl}${node.path}`,
          	changefreq: `daily`,
          	priority: 0.7,
        	};
      	}),
  	},
	},
  ],
};
```

The above GraphQL query fetches all the metadata of your blog as well all the existing routes. If you run this query in the GraphiQL playground, you will see an output similar to this.

```json
{
  "data": {
	"site": {
  	"siteMetadata": {
    	"siteUrl": "https://lelouchb-gatsby-starter-blog.netlify.app"
  	}
	},
	"allSitePage": {
  	"nodes": [
    	{
      	"path": "/posts/markdown-syntax-guide"
    	},
    	{
      	"path": "/posts/my-first-post"
    	},
    	{
      	"path": "/dev-404-page/"
    	},
    	{
      	"path": "/404/"
    	},
    	{
      	"path": "/"
    	},
    	{
      	"path": "/404.html"
    	}
  	]
	}
  },
  "extensions": {}
}
```

You can test this sitemap by running the following command in the project's root directory to create and serve your production build.

```bash
gatsby build && gatsby serve
```

Head over to [http://localhost:9000/sitemap.xml](http://localhost:9000/sitemap.xml)

![Sitemap.xml](https://i.imgur.com/ZTriFMM.png)

## Adding an RSS Feed

Let's say that I am an avid reader of your blog and I want to be notified of every new article that you publish so one way would be to visit your blog everyday and manually check for new articles. This task is tedious even for one blog but what if I want to be notified of many blog websites, manually checking is out of the box.

This is where the RSS feed comes to save the day, readers can use a RSS feed reader like [feedly](https://feedly.com ), [Miniflux](https://miniflux.net), [RSS Owl](http://www.rssowl.org/), etc. and subscribe to your RSS feeds and be updated with latest articles. 

Here is an example of someone subscribing to this starter blog RSS feed.

![Subscribe RSS Feed on Feedly](https://i.imgur.com/W2A6iTu.png)

Earlier in this tutorial, you added an RSS feed icon in the footer that points to the `/rss.xml` route that didn’t exist yet. To create the RSS feed, you will use the [`gatsby-plugin-feed`](https://www.gatsbyjs.com/plugins/gatsby-plugin-feed/) plugin.

```bash
npm install gatsby-plugin-feed
```

Stop your development server and update the `gatsby-config.js` file to include the `gatsby-plugin-feed` plugin.

```jsx
{
  resolve: `gatsby-plugin-feed`,
  options: {
	query: `
  	{
    	site {
      	siteMetadata {
        	title
        	description
        	siteUrl
        	site_url: siteUrl
      	}
    	}
  	}
	`,
	feeds: [
  	{
    	serialize: ({ query: { site, allMdx } }) => {
      	return allMdx.edges.map(edge => {
        	return Object.assign({}, edge.node.frontmatter, {
          	description: edge.node.excerpt,
          	date: edge.node.frontmatter.date,
          	url:
            	site.siteMetadata.siteUrl +
            	`/posts/` +
            	edge.node.frontmatter.slug,
          	guid:
            	site.siteMetadata.siteUrl +
            	`/posts/` +
            	edge.node.frontmatter.slug,
          	custom_elements: [{ "content:encoded": edge.node.html }],
        	})
      	})
    	},
    	query: `
      	{
        	allMdx(
          	sort: { order: DESC, fields: [frontmatter___date] },
        	) {
          	edges {
            	node {
              	excerpt
              	html
              	frontmatter {
                	title
                	date
                	slug

              	}
            	}
          	}
        	}
      	}
    	`,
    	output: "/rss.xml",
    	title: "Gatsyby Starter Blog RSS Feed",
  	},
	],
  },
},
```

There are two GraphQL queries in the above code: one for the site metadata and the other for all the posts. Like `gatsby-plugin-sitemap`, you will need to create a production build to see this plugin in action.

```bash
gatsby build && gatsby serve
```

Head over to [http://localhost:9000/rss.xml](http://localhost:9000/rss.xml), to see how the RSS feed will look.

![RSS Feed](https://i.imgur.com/LySUh8v.png)

Make sure to update the `siteUrl` in the `gatsby-config.js` file before deploying your blog so that the RSS feed’s URL is correct.

## Finishing the Starter
At this point, you have created a working Gatsby blog, but you still have one more step to make it a shareable **Gatsby starter**. [According to official Gatsby documentation](https://www.gatsbyjs.com/docs/creating-a-starter/#basic-requirements), a starter should have a few specific files to work properly.

First, add a [README.md](https://github.com/lelouchB/gatsby-starter-blog/blob/main/README.md) to your project. This should contain a screenshot of the starter and a thorough explanation for users to configure and customize it.

Next, add a [License](https://github.com/lelouchB/gatsby-starter-blog/blob/main/LICENSE) to your project. [BSD Zero Clause](https://opensource.org/licenses/0BSD) is generally preferred for Gatsby starters. 

Finally, update the `package.json` file to include the license, description, author name, version, etc.  You can see this starter’s `package.json` [here](https://github.com/lelouchB/gatsby-starter-blog/blob/main/package.json).

Now you can [submit](https://gatsbyjs.com/contributing/community-contributions/) your starter to the official Gatsby registry or simply share your starter with other developers on GitHub.

## Summary

In this tutorial, you learned how to build a Gatsby starter from scratch using MDX, Styled Components, and various Gatsby plugins. This starter included blog posts, an author bio, search engine optimization plugins, an RSS feed, and more. Using this starter, other developers will be able to build their own Gatsby projects much faster.

You can explore the source code of this project on [GitHub](https://github.com/lelouchB/gatsby-starter-blog), or if you want to use the starter created here, run the following in your terminal.

```bash
gatsby new my-gatsby-blog https://github.com/lelouchB/gatsby-starter-blog
```

If you're inspired to add features yourself, please do share and [tag me](https://twitter.com/noharashutosh) – I'd love to hear about them!



