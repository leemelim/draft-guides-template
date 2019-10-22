# Contributing to the Kabanero.io Guides
Each guide resides in its own repository and is dynamically pulled into kabanero.io via the build process. The content of the guide can be written in HTML, markdown, or AsciiDoc formats- AsciiDoc is preferred.

## Get Started

1. Create a repository for your guide in the Kabanero-io Org.
   * **Make sure `draft-guide-` is appended to the beginning of the repo name**. `draft-` ensures it will not get published to the site. `guide-` ensures our build process will pull in the guide during build.
   * If you need help opening a repository, create  an issue in this repository.
1. Ensure permissions are set in repository settings
   * `information-dev` team gets **Maintain** access
   * `kababero-website-team` team gets **Admin** access
1. Ensure master branch is protected
   * Under **Settings -> Branches**
      * Click **Add Rule** and enter `master` for the master branch
         * Check the box for: `Require pull request reviews before merging`
         * Check the box for:  `Include Administrators`

### Front Matter

The following front matter variables must be set as the first thing in each asciidoc:
```
---
permalink: /guides/appsody-getting-started/
---
:page-layout: guide
:page-duration: 40 minutes
:page-releasedate: 2019-09-19
:page-description: Explore how to use the Appsody CLI to create, run, update, deploy, and deliver cloud native microservices.
:page-tags: ['Appsody', 'Java', 'MicroProfile', 'Collection']
:page-guide-category: collections
= Your Guide Title
```

* **permalink**
   * The naming convention for `permalink` is `/guide/` followed by the GitHub repository name (do not include `guide-`)
      * For example, the appropriate `permalink` for https://github.com/kabanero-io/guide-appsody-get-started/ would be `/guides/appsody-get-started/`
      * This eliminates guide URL conflicts for guides as GitHub won't allow two repositories with the same name.

* **page-layout**
   * The layout for the content of the guide. `guide` is the normal layout.
   * `layout` could also be `guide-multipane`,  which renders that code column to show code on the side.
* **page-duration**
   * The expected time it would take a reader to complete the guide.
* **page-releasedate**
   * The expected release date of the guide. Do not put this date in the future, its okay if the guide doesn't go out exactly on that date.
* **page-description**
   * A description of your guide. What the user would expect to learn upon completing this guide.
* **page-tags**
   * Tags related to the guide. See approved tags below.
* **page-guide-category**
   * A single category for this guide. The categories map to the headers/rows on the /guides page.
* **=**
   * A title for your guide.

#### Approved Tags
* Collection
* Nodejs
* Express
* Java
* MicroProfile
* Spring
* Spring Boot
* Tomcat
* Appsody
* CLI

#### Approved Categories
* none

More categories will be added

### Add Images to your Guide

If you want to add images to your guide you can put them in your guide repository.

* Image Location
   * Create a dir in your guide repositoy called `assets` and put them in there.
      * These images get copied over to the sites `src/main/content/img/guide/` dir during build.

* Image Naming
   * You should include the name of your guide in the name your image to prevent image naming conflicts from other guide repositories.

* Image Reference
   * You can reference the image in your AsciiDoc file like the following example:
      * `image::/img/guide/name_of_your_image.png[link="/img/guide/name_of_your_image.png" alt="Your image alt text"]`

# Render a Guide locally

Once you have your local development environment setup you can render guides as your write them.

## Prereqs
* [Local development setup](https://github.com/kabanero-io/kabanero-website/blob/master/CONTRIBUTING.md#local-development-setup)

## Render your guide

1. Create a new dir called `guides` under `src/main/content/`
1. Inside the new `guides` dir, make a new folder called `guide-name_of_your_guide`
1. Create the `README.adoc` in that newly created folder and place your content in there.
1. Copy any images that you are using in your guide to the `src/main/content/img/guide` directory.
   * Note- this is done automatically during website build, but is needed during local development.
1. Start your local dev server and go to `https://localhost:4000/guides` to see all the guides rendered.
