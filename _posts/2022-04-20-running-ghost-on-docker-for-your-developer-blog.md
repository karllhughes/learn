---
layout: post
title: Running Ghost on Docker for Your Developer Blog
description: Ghost is an open source Node.js blogging platform. It’s simple to
  get started, and offers a paid hosting option. In this article, we'll show the
  reader how to install and use Ghost inside a Docker container so that you can
  host and share the deployment with ease.
categories: platforms
cta: Playbook
author: Arek Nawo
date: 2022-04-20T13:51:35.690Z
img: /assets/posts/ghost-logo.png
---
[Ghost](https://ghost.org/) is one of the most popular open source blogging platforms. It boasts powerful features for almost everything related to blogging, such as editing, publishing, email newsletters, and offering paid subscriptions. Ghost offers pre-made themes that you can use to set up your blog quickly, but thanks to its extensive API, you can also use it as a headless CMS for your custom frontend.

You can install Ghost in [several ways](https://ghost.org/docs/install/), one of which is [Docker](https://www.docker.com/).

Deploying Ghost with Docker has many advantages. With Docker containers, you get a flexible and easily reproducible way to run your blog. It allows you to spin up another instance quickly when one fails or updates. On top of that, you get the same setup experience, regardless of if you’re in a development or production environment.

This article will guide you through the entire process of setting up a Ghost blog with Docker. You can find all configuration files from this tutorial in [this GitHub repo](https://github.com/areknawo/Running-Ghost-on-Docker-for-Your-Developer-Blog).

## Ghost’s Features

Before diving in, let’s first explore some of Ghost’s features in depth.

### Simplicity and Ease of Use

As you’ll see in a bit, Ghost is very simple to set up, especially with the pre-made Docker image. On top of that, the other parts of the Ghost experience are easy to grasp, too. Everything from the content editor to the settings panel has a clean, minimal design.

### Editing and Publishing Experience

The Ghost editor is one of the best in the business. It provides everything you need to create excellent content, including:

-   Floating formatting menu.
-   Image, HTML, and other content blocks.
-   Media embeds for Twitter, YouTube, CodePen, and more.
-   Markdown shortcuts.
-   Reusable content snippets.

When you’re done writing, publishing is just a matter of providing some metadata and hitting the **Publish** button.

### Email Newsletters

In addition to blogging, Ghost can also be used for email newsletters. With its built-in email design editor, members list, email analytics, and [Mailgun](https://www.mailgun.com/) integrations, you get a feature-complete solution for running your own newsletter right from your blog.

### Subscriptions and Memberships

Thanks to its [Stripe](https://stripe.com/) integration, a custom API, and a member administration dashboard, Ghost has everything you need to implement paid subscriptions and monetize your blog. You can create anything from a straightforward donation system to paywalled content or premium newsletters. 

## Setting Up Ghost with Docker

This guide assumes you’re running Ubuntu 18.04 or newer. To run Ghost in Docker, a minimum of 1 GB of RAM and a decent CPU are recommended.

### Installing Docker

Before installing Ghost, you’ll need to install [Docker Engine](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/). Be sure to uninstall any previous versions of Docker Engine that might be installed on your system:

```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```

Use apt to install all packages required by Docker:

```bash
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

Add Docker’s official GPG key to verify the integrity of the Docker packages:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

Set up Docker’s stable repository as a package download source:

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker Engine and Docker Compose, then verify the installation:

```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose
docker --version
docker-compose --version
```

If everything was set up correctly, you should see version numbers for Docker Engine and Docker Compose in your terminal.

### Running the Ghost Image

With Docker ready, you can now use it to download and run the Ghost image.

#### For Development

This is the easiest way to get the Ghost image up and running for development purposes. With this setup, the container is stateless, meaning all data will be lost if anything happens to it. Also, by default, the Ghost blog is using an [SQLite](https://sqlite.org/) database. 

Run the Ghost image using the following command:

```bash
docker run -d --name my-ghost-blog -e url=http://localhost:2368 -p 2368:2368 ghost
```

This will create a container named `my-ghost-blog` using the [official Ghost image](https://hub.docker.com/_/ghost) provided by the Docker community. The Ghost blog will be accessible on port `2368`.

While convenient and great for development purposes, this setup isn’t ready for production. For that, a bit more configuration is required.

#### For Production

Start by creating a dedicated directory, like `my-ghost-blog`, and a `docker-compose.yml` file inside it:

```bash
mkdir my-ghost-blog
cd my-ghost-blog
touch docker-compose.yml
```

Inside the file, define the configuration for Docker containers:

```yaml
version: "3.3"
services:
  ghost:
    image: ghost:latest
    restart: always
    ports:
      - "2368:2368"
    depends_on:
      - db
    environment:
      url: http://localhost:2368
      database__client: mysql
      database__connection__host: db
      database__connection__user: ghost
      database__connection__password: ghostdbpass
      database__connection__database: ghostdb
    volumes:
      - /home/ghost/content:/var/lib/ghost/content

  db:
    image: mariadb:latest
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: your_mysql_root_password
      MYSQL_USER: ghost
      MYSQL_PASSWORD: ghostdbpass
      MYSQL_DATABASE: ghostdb
    volumes:
      - /home/ghost/mysql:/var/lib/mysql
```

With this config, an additional [MySQL](https://www.mysql.com/) database container will be created using a [MariaDB](https://mariadb.org/) image. Additionally, a dedicated volume is added for the Ghost blog to provide stateful storage.

Now, execute the configuration with `docker-compose up -d`. You can now see the Ghost blog on port `2368`.

![Ghost with default Casper theme](https://i.imgur.com/BRs78Hk.png)

### Setting Up Your Ghost Blog

To get started with Ghost, go to `http://localhost:2368/ghost`. This is where your admin panel will be located. Going there for the first time, you should see a setup screen like the below:

![Ghost admin setup](https://i.imgur.com/usy9bBi.png)

Fill out the form, and you’ll be greeted with the dashboard.

![Ghost dashboard](https://i.imgur.com/wZa9Oo8.png)

To create your first post, click the **+** button next to **Posts**, which will take you to the post editor.

![Ghost editor](https://i.imgur.com/RJCMfxO.png)

From inside the editor, you can write your blog post and set all of its metadata. When you’re done, click **Publish** to make your post public.

### Exposing and Securing the Ghost Blog

Now, while the Ghost blog is up and running, there’s still some setup to be done on the backend. You’ll have to expose the app for outside access with a proxy like [Nginx](https://www.nginx.com/) and secure it with an SSL certificate. This process will require a domain, which we'll refer to as `example.com`.

#### Obtaining an SSL Certificate

To obtain an SSL certificate for your domain, you’ll first have to install the latest [Certbot](https://certbot.eff.org/) package with the [Snapd package installer](https://snapcraft.io/docs/installing-snapd).

First, ensure Snapd is up-to-date and that no older versions of Certbot are installed:

```bash
sudo snap install core
sudo snap refresh core
sudo apt remove certbot
```

Next up, install Certbot and create a symlink to its installation path to ensure it's accessible through the `certbot` command:

```bash
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

Finally, run the following command to generate and download the certificate for your domain:

```bash
sudo certbot certonly --standalone -d example.com
```

With the SSL certificate ready, you can move on to Nginx.

#### Creating Custom Nginx Docker Image

In this example, you’ll see how to run Nginx as a separate container with Docker Compose.

To get started, create a new `nginx` folder:

```bash
mkdir nginx
cd nginx
```

You have to alter the official Nginx image to include a custom Nginx config. To do so, create a file called `ghost.conf` to hold the custom Nginx config:

```text
server {
  listen 80;
  listen [::]:80;
  server_name example.com;
  # Useful for Let's Encrypt
  location /.well-known/acme-challenge/ { root /usr/share/nginx/html; allow all; }
  location / { return 301 https://$server_name$request_uri; }
}

server {
  listen 443 ssl http2;
  listen [::]:443 ssl http2;
  server_name example.com;
    
  access_log /var/log/nginx/ghost.access.log;
  error_log /var/log/nginx/ghost.error.log;
  client_max_body_size 20m;

  ssl_protocols TLSv1.2 TLSv1.3;
  ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384;
  ssl_prefer_server_ciphers on;
  ssl_session_timeout 1d;
  ssl_session_cache shared:SSL:10m;

  ssl_certificate     /etc/letsencrypt/live/example.com/fullchain.pem;
  ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;

  location / {
    proxy_set_header Host $http_host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-Proto https;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_pass http://ghost:2368;
  }
}
```

This configuration exposes the Ghost app running in a separate container (at `http://ghost:2368`), and includes the necessary configuration for the SSL certificate to work correctly.

Now, create a new Dockerfile where you’ll alter the Nginx default image:

```bash
FROM nginx:latest
RUN rm /etc/nginx/conf.d/default.conf
COPY ghost.conf /etc/nginx/conf.d
```

With the Dockerfile ready, you can now return to your Docker Compose configuration.

#### Updating the Docker Compose Config

If your Ghost blog is still running, you should first stop it with the `docker-compose down` command. As the configuration has already had a volume attached, all the data will persist through the reset.

Update the `docker-compose.yml` file to add a separate Nginx container, and remove the `ports` property from the `ghost` container:

```text
version: '3.3'
services:

  ghost:
    image: ghost:latest
    restart: always
    depends_on:
      - db
    environment:
      url: https://example.com
      database__client: mysql
      database__connection__host: db
      database__connection__user: ghost
      database__connection__password: ghostdbpass
      database__connection__database: ghostdb
    volumes:
      - /home/ghost/content:/var/lib/ghost/content

  db:
    image: mariadb:latest
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: your_mysql_root_password
      MYSQL_USER: ghost
      MYSQL_PASSWORD: ghostdbpass
      MYSQL_DATABASE: ghostdb
    volumes:
      - /home/ghost/mysql:/var/lib/mysql
  nginx:
    build:
      context: ./nginx
      dockerfile: Dockerfile
    restart: always
    depends_on:
      - ghost
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - /etc/letsencrypt/:/etc/letsencrypt/
      - /usr/share/nginx/html:/usr/share/nginx/html
```

With that done, run the app with `docker-compose up -d` once again. If everything is set up correctly, you should see your Ghost blog under `https://example.com`.

### Deployment Options

Thanks to Docker’s popularity and flexibility, there are tons of options to choose from when it comes to hosting your app. A well-designed containerized app can run everywhere from virtual private servers to dedicated Docker cloud environments or Kubernetes clusters.

Some of the most popular Docker deployment platforms include:

-   [Amazon ECS](https://aws.amazon.com/ecs/)
-   [DigitalOcean Managed Kubernetes](https://www.digitalocean.com/products/kubernetes)
-   [Google Cloud Run](https://cloud.google.com/run)
-   [Microsoft Azure ACI](https://azure.microsoft.com/en-us/services/container-instances/)

## Conclusion

In this post, you've learned how to leverage the flexible and reproducible architecture allowed by Docker to set up your own Ghost blog. The only thing left now is to fill it with excellent technical content. That’s where Draft.dev steps in.

[Draft.dev](https://draft.dev/) is a company that provides high-quality technical content for all your needs. [Check out their website](https://draft.dev/) and schedule a call to get your technical blogging game going!
