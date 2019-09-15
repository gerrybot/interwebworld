---
author: "interweb"
date: 2018-07-19
draft: false
linktitle: The Damn Giants Causeway
title: The Damn Giants Causeway
categories: [
    "Northern Ireland",
]
tags: [
    "Geology",
    "Netlify"
]
weight: 10
featureimage: susannaDrury.jpg
---


## Finn McCool FM

The hot new thing in web development is actually pretty old: static websites. But these are static sites with a twist: using modern web development tools to build and deploy a complete website.

{{< image name="susannaDrury.jpg" alt="{{Trying to embed an image}}" caption="My caption for this image" >}}

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
