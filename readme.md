---
layout: default-layout.njk
title: ReadMe
---

# Checklist for 11ty & Netlify presentation

[![Netlify Status](https://api.netlify.com/api/v1/badges/1c0fda01-75fa-47e7-98e4-c480b4324031/deploy-status)](https://app.netlify.com/sites/demoblog/deploys)

[**Demo of 11ty & Netlify on YouTube**](https://www.youtube.com/watch?v=ozTesGh0l74)

Mini site available at https://demoblog.netlify.com/

* [11ty Docs](https://www.11ty.io/)
* [Netlify Docs](https://www.netlify.com/docs/welcome/)

## Before Presentation

* [ ] Delete old Github repo
* [ ] Delete old Netlify site
* [ ] Delete old local folder
* [ ] Set zoom on Chrome and VS Code
* [ ] Chrome Dev tools in Docked to bottom
* [ ] Set visible monitor as main display to capture Alt + Tab
* [ ] Open Github and Netlify - Log in to both
* [ ] Disable notifications / sound
* [ ] One trial run on conference WiFi

## Presentation Steps

* Introduce Agenda

#### Repo Setup

* [0:15] Create github Repo - "Demo Blog"
  * Select Gitignore - Node
* [0:48] Clone Locally
  * Copy Github URL
  * Switch to VS code terminal
  * Clone locally `git clone url`
  * `cd` into folder
* [1:09] Open vs code in folder `code . -r`
* [1:30] Add npm `npm init -y`
* [1:40] Add eleventy `npm i @11ty/eleventy` (**note**: org/repo)
  * this will take a minute 
  * start on content or give more overview

#### 11ty Setup

* [1:55] Add Markdown content
  * index.md - (**note**: lowercase important)
  * about.md
* [3:40] Build site locally `npx eleventy`
  * look at build folder and generated html
  * introduce *folder/index.html* structure
* [4:44] Run site locally `npx eleventy --serve`
  * Open browser
  * Manually navigate to `/about/` page
* Achieved minimum viable site! 🎉

#### Git Push

* [5:38] add `_site` to `.gitignore`
* [6:05] git commit and push
* [6:33] Confirm commit made it to GitHub

#### Netlify Setup

* [6:49] Create netlify site
  * pick repo
  * pick eleventy defaults
* [7:38] View build process
* [7:52] Change site name 
  * [http://demoblog.netlify] if it's available - or audience suggestion
* [8:14] View site
* [8:25] Make one minor change and push
  * Look at build process and look at new site
  * Production site served off master
    * For SDLC, netlify also has feature branch deploys and PR deploys
    * Automic, Immutable Deployments - restore back at any point

#### Site Layout

* [9:45] Add `_includes` folder
  * Add nunjucks `default-layout.njk`
  * Introduce nunjucks - html + curly brackets templating
* [11:00] Point content files at layout
  * Add Yaml Frontmatter to both pages
  * Introduce Yaml - key value pair surrounded by triple hyphens
  * We don't need the `_includes` path, 11ty looks there by default

  ```yaml
  ---
  layout: default-layout.njk
  ---
  ```

* [11:47] Add content to body `{{content | safe}}`
* [12:23] Add html layout
  * Add HTML structure `<html>`, `<head>`, `<body>`
  * Add `<h1>` with site name like "VT CC Blog" (to prove we're on layout)
* [12:49] View Site - Site name should appear

#### Page Titles

* [13:10] Add title to each yaml block
* [13:41] Add `{{title}}` to `<h2>` and `<title>` elements
* [13:59] View Site - Head title should appear

#### Navigation

* [14:13] Add navigation to layout page

  ```pug
  nav
    ul
      li a(href='/') home
      li a(href='/about/') about
  ```

* [14:48] View site - click between pages

#### Styles

* [15:20] Add styles in dev tools

  ```css
  body {
      max-width: 50rem;
      margin: 0 auto;
  }
  nav ul {
      list-style: none;
      display: flex;
      background:aliceblue
  }

  nav ul li {
      padding: 5px
  }
  ```

  * Copy to clipboard
* [16:57] Introduce asset pipeline
  * Now we need a way to get them into our site
  * We could inline them into layout page, but let's say we want to author stylesheet externally
  * By default, 11ty only puts built content into the output directory
* [17:28] Create `assets` folder
  * Create `styles.css` and paste in styles
* [17:45] Add 11ty config
  * Create `.eleventy.js`

  ```js
  module.exports = function (eleventyConfig) {
    eleventyConfig.addPassthroughCopy('assets')
  }
  ```

* [18:41] Restart eleventy (config only read on startup)
  * Confirm assets folder is built into `_site`
* [19:13] Add stylesheet to layout `<link rel="stylesheet" href="/assets/style.css">`
* [19:45] View Site - Styles are applied

#### Netlify Features

* [20:26] Push changes
* [20:42] Go to Netlify
  * Post-Processing / Asset-Optimization
* [21:04] Buy domain

[0:15]: https://www.youtube.com/watch?v=ozTesGh0l74&t=15
[0:48]: https://www.youtube.com/watch?v=ozTesGh0l74&t=48
[1:09]: https://www.youtube.com/watch?v=ozTesGh0l74&t=69
[1:30]: https://www.youtube.com/watch?v=ozTesGh0l74&t=90
[1:40]: https://www.youtube.com/watch?v=ozTesGh0l74&t=100
[1:55]: https://www.youtube.com/watch?v=ozTesGh0l74&t=115
[3:40]: https://www.youtube.com/watch?v=ozTesGh0l74&t=220
[4:44]: https://www.youtube.com/watch?v=ozTesGh0l74&t=284
[5:38]: https://www.youtube.com/watch?v=ozTesGh0l74&t=338
[6:05]: https://www.youtube.com/watch?v=ozTesGh0l74&t=365
[6:33]: https://www.youtube.com/watch?v=ozTesGh0l74&t=393
[6:49]: https://www.youtube.com/watch?v=ozTesGh0l74&t=409
[7:38]: https://www.youtube.com/watch?v=ozTesGh0l74&t=458
[7:52]: https://www.youtube.com/watch?v=ozTesGh0l74&t=472
[8:14]: https://www.youtube.com/watch?v=ozTesGh0l74&t=494
[8:25]: https://www.youtube.com/watch?v=ozTesGh0l74&t=505
[9:45]: https://www.youtube.com/watch?v=ozTesGh0l74&t=585
[11:00]: https://www.youtube.com/watch?v=ozTesGh0l74&t=660
[11:47]: https://www.youtube.com/watch?v=ozTesGh0l74&t=707
[12:23]: https://www.youtube.com/watch?v=ozTesGh0l74&t=743
[12:49]: https://www.youtube.com/watch?v=ozTesGh0l74&t=769
[13:10]: https://www.youtube.com/watch?v=ozTesGh0l74&t=790
[13:41]: https://www.youtube.com/watch?v=ozTesGh0l74&t=821
[13:59]: https://www.youtube.com/watch?v=ozTesGh0l74&t=839
[14:13]: https://www.youtube.com/watch?v=ozTesGh0l74&t=853
[14:48]: https://www.youtube.com/watch?v=ozTesGh0l74&t=888
[15:20]: https://www.youtube.com/watch?v=ozTesGh0l74&t=920
[16:57]: https://www.youtube.com/watch?v=ozTesGh0l74&t=1017
[17:28]: https://www.youtube.com/watch?v=ozTesGh0l74&t=1048
[17:45]: https://www.youtube.com/watch?v=ozTesGh0l74&t=1065
[18:41]: https://www.youtube.com/watch?v=ozTesGh0l74&t=1121
[19:13]: https://www.youtube.com/watch?v=ozTesGh0l74&t=1153
[19:45]: https://www.youtube.com/watch?v=ozTesGh0l74&t=1185
[20:26]: https://www.youtube.com/watch?v=ozTesGh0l74&t=1226
[20:42]: https://www.youtube.com/watch?v=ozTesGh0l74&t=1242
[21:04]: https://www.youtube.com/watch?v=ozTesGh0l74&t=1264
