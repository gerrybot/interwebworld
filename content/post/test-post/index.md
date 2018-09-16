---
author: "Gerard McGarry"
date: 2018-06-19
linktitle: Building A Site With Hugo, Github and Netlify
title: Building A Site With Hugo, Github and Netlify
categories: [
    "Tutorials",
]
tags: [
    "Hugo",
    "Netlify",
    "Github",
]
weight: 10
featureimage: test-image.jpg
---


## Introduction

The hot new thing in web development is actually pretty old: static websites. But these are static sites with a twist: using modern web development tools to build and deploy a complete website.

{{< image name="test-image.jpg" alt="{{Trying to embed an image}}" caption="My caption for this image" >}}

I've been hearing a lot about [Hugo](https://gohugo.io/) these days - a superfast static site generator. Static has a lot of advantages: you don't have to worry about resource-hungy server-side technologies such as PHP or MySQL. You don't have to worry about Content Management Systems, frequent patching and security updates. And because you're dealing with static pages, you don't have to concern yourself with caching and other types of server optimisation. Awesome, right?

## The Problem with Hugo

Coming into the world of Hugo, the biggest problem for me was piecing it all together.

The goal was developing the site locally on my laptop, then *somehow* getting the latest version of the site pushed up to the web. The problem is, where do you begin?

When you listen to people talk about Hugo, the Holy Grail of static is Hugo paired with Github and Netlify. But how dows it all come together?

1. *Hugo*: You run Hugo locally on your machine, build and refine your site, add new content.
2. *Guthub*: Github hosts repositories online. You create a repository on Github, then push your development build from your laptop when you're ready to deploy it to the web.
3. *Netlify*: Netlify is a radically cool hosting platform. It monitors your Github repository for new commits. When it finds new commits, it imports them, runs a Hugo build and hosts the resulting static site.

Hopefully that explains how all three pieces work together. Let's walk through a typical Hugo/Netlify/Github deployment setup.

## Build a local Hugo site

Let's start with a local Hugo build. 

``` bash
hugo new site interweb
```
## Add a netlify.toml file to your Hugo site

**Why are we doing this?** Because it helps us specify the Hugo version that Netlify will use to compile your site. If we prep this in advance, we don't have to worry about it later. Example content is as follows - update your Hugo version to the latest:

```
[build]
publish = "public"
command = "hugo"

[context.production.environment]
HUGO_VERSION = "0.40.1"
```


Without the netlify.toml file, the build will most likely fail.
## Connect your local Hugo to Guthub

Enter your Hugo root directory

```
git init
touch archetypes/.gitkeep content/.gitkeep layouts/.gitkeep static/.gitkeep data/.gitkeep
git add .
git commit -m 'First commit'
git remote add origin https://github.com/gerrybot/interwebworld
git remote -v
git push origin master
```


## Connect Github to Netlify
You're already logged into Github, so go to the Netlify homepage and sign in with your Github account.

1. Select *New site from Git*
2. Click the *Github* option
3. Select the repository you just created (mine was interwebworld)
4. In the Deploy settings page, set the  Branch to "master", and use ```hugo``` as the basic build command, and ```public``` as the Publish directory.
5. Click *Deploy site*

## Change Netlify Site Name

By default, all Netlify sites start out on a subdomain on netlify.com. Netlify assigns a random subdomain name, but you can customize this.

## Map a custom domain name to Netlify

Click on the Overview tab for your Netlify site and click Domain Settings. This will allow you to add a custom domain. In my case the custom domain will be interwebworld.co.uk.

Click the **Add Custom Domain** button. Add the URL of the custom domain. For my site, it was interwebworld.co.uk.

I opted to create a new DNS zone on Netlify for my domain. This means Netlify is the default handler for requests to interwebworld.co.uk. Awesome!

After that, you must go to wherever you've registered your domain and point the DNS records to Netlify. Give this the standard amount of Internet patience to allow DNS settings to replicate around the web, etc.

## Set up HTTPS with LetsEncrypt

Netlify handles all of the setup of this. All you have to do is browse to Domain Management/HTTPS. First, check DNS verification. You might need to wait until DNS has propagated though. Be patient, hombre. 

Once you get this done, enable Force HTTPS. This is best for SEO reasons and ensures all your visitors are served over HTTPS, keeping Google happy and giving your readers a better experience.

## Continuous deployment

Provided you've handled everything correctly, Netlify will monitor your Github repository for new commits and then build and deploy them automatically.

On your local computer, when you're ready to push a new version of the site to Github, go to the root of your Hugo instance and enter the following commands:

```
git add .
git commit -m 'Update comment'
git remote -v
```

This will stage and upload your changes to Github. Netlify will then kick off a build of the site and moments later it will be available on the custom domain that you set up. Ta-da!!! #JazzHands

## References

1. The [best damn Hugo tutorial I have ever read](https://www.sarasoueidan.com/blog/jekyll-ghpages-to-hugo-netlify/).

dns1.p02.nsone.net