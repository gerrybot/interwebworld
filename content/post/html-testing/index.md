---
author: "Interweb"
date: 2019-09-10
linktitle: I'm testing HTML elements with this theme
title: Testing the HTML elements in the Typewriter theme
categories: [
    "Tutorials",
]
tags: [
    "Hugo",
    "Netlify",
    "Github",
]
weight: 10
featureimage: digital.jpg
---


## Testing HTML Elements

This post will contain a number of common HTML elements for the purpose of testing the CSS rules within the Typewriter theme.

{{< image name="digital.jpg" alt="Trying to embed an image" caption="My caption for this image" >}}

This is a test of a link: [a lot about Hugo](https://gohugo.io/)

## Lists

### Unordered lists

* First point
* Second point
* I thought a lot more about the third point

### Ordered lists

1. Point #1
2. Point #2
3. Another epiphany of a third point

Coming into the world of Hugo, the biggest problem for me was piecing it all together.

1. *Hugo*: You run Hugo locally on your machine, build and refine your site, add new content.
2. *Guthub*: Github hosts repositories online. You create a repository on Github, then push your development build from your laptop when you're ready to deploy it to the web.
3. *Netlify*: Netlify is a radically cool hosting platform. It monitors your Github repository for new commits. When it finds new commits, it imports them, runs a Hugo build and hosts the resulting static site.

Hopefully that explains how all three pieces work together. Let's walk through a typical Hugo/Netlify/Github deployment setup.

## Build a local Hugo site

Let's start with a local Hugo build. 

``` bash
hugo new site interweb
```
## Code snippet

**Why are we doing this?** Because it helps us specify the Hugo version that Netlify will use to compile your site. If we prep this in advance, we don't have to worry about it later. Example content is as follows - update your Hugo version to the latest:

```
[build]
publish = "public"
command = "hugo"

[context.production.environment]
HUGO_VERSION = "0.40.1"
```

# Heading Level 1

## Heading Level 2

### Heading Level 3

#### Heading Level 4

##### Heading Level 5