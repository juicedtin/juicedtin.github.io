---
title: "Setup of a Github Pages Jekyll Website"
excerpt: "How I setup this website using Jekyll and Github Pages!"
---

## Contents

1. [Introduction](#Introduction)
2. [Github Pages](#GithubPages)
3. [Markdown](#Markdown)
4. [Pages and Markdown](#PagesMarkdown)

### Introduction <a name="Introduction"></a>

Before this class started, I heard a lot about Github Pages websites being used by other majors for portfolios and such - and now that BME66 has given me an excuse to create a website of my own, I've taken it upon myself to dive deep into the horrors of Ruby, Jekyll, HTML/CSS/SASS, and everything in between. For those who would like to follow this same path, I'm documenting everything I've done - hope it helps!

### Github Pages <a name = "GithubPages"></a>

GitHub Pages is what I used to host my website - but it's a little weird in how its set up initially. I found the official [Github Pages](https://docs.github.com/en/pages)and [Jekyll](https://jekyllrb.com/docs/) documentation very useful for answering questions and setting up the website. I've also used a popular theme from the Github community known as [Minimal Mistakes]("https://github.com/mmistakes/minimal-mistakes") for the general theming and heavy-duty HTML/CSS for the overall site layout. Minimal Mistakes also creates a bunch of default layouts, which are really nice to use so I don't have to spend time making my own. After forking the above repository, I have something that looks a little like this: 
<center>
<image src="assets\images\P1\GithubRepo.jpg" alt="Screenshot of Github repo path structure"/>
</center>
\_config.yml is especially important here to setup subpages, as I decided to group all of my future assignments into a "Collection" rather than separate pages. Thus, I added a folder \_bme66 to my website assets and defined it in a collection:

~~~yaml
#Collections
collections:
  bme66:
    output: true
    permalink: /:collection/:path/
~~~
with the following default definitions
~~~yaml
  # _bme66
  - scope:
      path: ""
      type: bme66
    values:
      layout: single
      author_profile: false
      share: true 
~~~
Here, the various values define various things about the category (and all the pages that will be going into it). Firstly, a `path` denotes that the Jekyll engine should process all the pages in the folder (yup, we want that). `type` is simply a designation to match the previously-defined collection. 

_Note that during this process, I've found that some markdown items weren't rendering correctly in Obsidian - so I copied over my "drafts" Obsidian vault into my pages to test the site rendering on localhost:4000 until I could get it right using the methods in [Pages and Markdown](#PagesMarkdown)_

I actually had a lot of problems with this section, as the setup of collections is very specific and if you get something wrong, Jekyll gets angry and doesn't render the website as you expect. I ended up having to split the website to get the collections to work - I redefined a new collections to the final config as depicted above. It turns out that my website wasn't compiling because I accidentally used an `=` instead of an `:` in the config file. 

Go figure. From now on, I think I should definitely keep a better eye on that syntax, especially as I make these files longer and longer for my future homeworks!

Anyway... now 

### Markdown <a name="Markdown"/></a>

First order of business - this page is written in Markdown, which is a really awesome, lightweight markup language that lets me make cool things like table of contents, etc. Because of the way the file structure works as I mentioned in the prior section, I can simply point my Markdown editor to 
Now in this folder, I can write all my assignments in <a href="https://www.markdownguide.org/basic-syntax/">Markdown</a>, using the syntax shown at the link. I had some problems initially learning the syntax, but I haven't documeted those issues here as I deemed that they weren't universalizable to those looking to replicate my process. I've attached the raw markdown code for this page as an example if people are looking to replicate the things I've made!

### Integrating Things Together <a name = "Integrate"></a>