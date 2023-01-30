---
title: "F1 &#124;&#124; Setting up This Website"
excerpt: "How I setup this website using Jekyll, Github Pages, and a dash of HTML!"
permalink: /bme66/F1
classes: wide
sidebar:
- title: Relevant Topics
  text:  Jekyll, Github Pages, Git version control, Markdown, HTML/CSS
---
- [Introduction ](#introduction-)
- [Github Pages ](#github-pages-)
- [Markdown ](#markdown-)
- [Integrating Things Together ](#integrating-things-together-)

## Introduction <a name="Introduction"></a>

Before this class started, I heard a lot about Github Pages websites being used by other majors for portfolios and such - and now that BME66 has given me an excuse to create a website of my own, I've taken it upon myself to dive deep into the horrors of Ruby, Jekyll, HTML/CSS/SASS, and everything in between. For those who would like to follow this same path, I'm documenting everything I've done - hope it helps!image.png

## Github Pages <a name = "GithubPages"></a>

GitHub Pages is what I used to host my website - but it's a little weird in how its initially set up. I found the official [Github Pages](https://docs.github.com/en/pages) and [Jekyll](https://jekyllrb.com/docs/) documentation very useful for answering questions and setting up the website. I've also used a popular theme from the Github community known as [Minimal Mistakes]("https://github.com/mmistakes/minimal-mistakes") for the general theming and heavy-duty HTML/CSS for the overall site layout. Minimal Mistakes also creates a bunch of default layouts, which are really nice to use so I don't have to spend time making my own. After forking the above repository, I have something that looks a little like this: 
![Screenshot of Github repo](/assets/images/P1/GithubRepo.png)
`_config.yml` is especially important here to setup subpages, as I decided to group all of my future assignments into a "Collection" rather than separate pages. Thus, I added a folder `_bme66` to my website assets and defined it in a collection:

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

_Note that during this process, I've found that some markdown items weren't rendering correctly in VSCode - so I tested the site rendering on localhost:4000 until I could get it right using the methods in [Integrating Things Together](#Integrate)_

I actually had a lot of problems with this section, as the setup of collections is very specific - if you get something wrong, Jekyll gets angry and doesn't render the website as you expect. It turns out that my website wasn't compiling because I accidentally used an `=` instead of an `:` in the config file. 

Go figure. From now on, I think I should definitely keep a better eye on that syntax, especially as I make these files longer and longer for my future homeworks.

Anyway... now that we have a collection set up, time to make the landing page - I decided to follow the documentation and use an inbuilt "gallery" theme that will display all the posts in a list-like fashion - this way, I don't even need to write any code for the display, and the theme *should* handle the rest. In case something breaks down the line, I've included the `_layout` folder that has the raw HTML/Liquid code - and if I make any edits, I will update this page accordingly!

~~~yaml
---
title: "BME66 Design Course"
layout: collection
permalink: /bme66/
collection: bme66
entries_layout: list
classes: wide
---
BME66 Design Homeworks, Projects, and Documentation!
~~~

This creates a landing page at the BME66 permalink, that had a grid layout to lay out all posts in the `_bme66` folder. Integrating this landing page into the general navigation is also a piece of cake - in `_data`, a folder called `navigation.yml` is read by the layouts to handle the sidebar at the top, so I just have to add this snippet to the end:
~~~yaml
  - title: "BME66"
    url: /bme66/
~~~
Now, to write my first post!

## Markdown <a name="Markdown"></a>

First order of business - this page is written in Markdown, which is a really awesome, lightweight markup language that lets me make cool things like table of contents, etc. Because of the way the file structure works as I mentioned in the prior section, I can simply point my Markdown editor to `_bme66` and go crazy.
Now in this folder, I can write all my assignments in <a href="https://www.markdownguide.org/basic-syntax/">Markdown</a>, using the syntax shown at the link. I had some problems initially learning the syntax, but I haven't documeted those issues here as I deemed that they weren't universalizable to those looking to replicate my process. If you would like to see the raw Markdown code (for those of you in my BME66 class, feel free to email me at my Tufts email). 

Although it's a little low-tech, I just used VSCode with it's integrated `Cntrl+K, V` rendering functionality to display Markdown. It's good enough for the job and doesn't require any extra downloads, which makes it easy to setup. It ends up looking something like this:
![VSCode Demonstration](/assets/images/P1/MDDemo.png)

Note the `YAML` header at the top between the `---`. This denotes the title, excerpt, and sidebar settings according to the theme syntax, so that this post will show up correctly on the `/bme66/` landing page. 
To get my title looking correct, I had to do some more Googling -  note the weird `&#124;` - this is HTML-speak to display special characters which includes pipes like "||". When I put a normal "||" character in my title, it showed up as blank. Similarly, anytime I want to use an underscore outside of "code mode" in Markdown, I have to follow it with a backslash: `\_` these are generally known as escape characters and are used frequently in markup languages.

## Integrating Things Together <a name = "Integrate"></a>

Now, I can put my website up on the web so everybody else can ~~bask in it's beautiful glorious presence~~ get up-to-date on all of my BME66 projects (and anything else I decide to make). First off, I have to set up Pages on Github as so:
![Github Pages Settings](/assets/images/P1/PagesSettings.png)

The repo itself will only be recognized as a valid site URL if it matches my username "juicedtin" exactly (i.e. in the format juicedtin.github.io as the repository name). This also means that the page deploys from the master branch, so I can always fork the repo if I want to make a draft or something, etc.

Pulling and pushing to deployment on Github is pretty slow overall (it takes about 45 seconds for the website to update from when I push locally) so it's annoying to check the front-end effects of anything I change on the back-end (non-Markdown stuff). Jekyll has a very nice way to get around this using the command `bundle exec jekyll serve`. I ran this though a Powershell instance out of my local folder - make sure to install Ruby, Jekyll, and all required dependencies for Minimal-Mistakes (otherwise the engine will probably protest with error messages). Doing this hosts a local instance of your website on `localhost:4000` (which you can access through any browser) that updates in real-time with any file change. It builds in about 3 seconds, and renders everything exactly as you would see it on the actual webpage:
![Bundle exec jekyll serve implementation, example output](/assets/images/P1/BundleExec.png)

Once everything's set up, I can just push to Github, make sure nothing breaks during the build process, and that's that. An awesome Github Pages website, hosted with the Minimal-Mistakes theme, ready to be populated with BME66 projects. 

## Postscript Update 1: Making a Splash Homepage

Justin from the future's writing this one! After I finally set up the collections and navigation correctly, I realized that I wanted the main home landing page to look a little cooler than it did. So, I set up my own custom landing page using a different layout `splash` through a custom Markdown landing page that I've named `index.md`. Using the following header:
~~~yaml
layout: splash
permalink: /
hidden: true
header: 
    overlay_image: /assets/images/Landing.png
    caption: "Photo credit: [**SouredApple**](https://twitter.com/SouredApple)"
excerpt: "Tufts Biomedical Engineering, Class of 2024"
descrip: 
  - excerpt: "Welcome to my portfolio! Here you should be able to find all of the things I've designed and made over my time here at Tufts, along with any other random things I'd like to put up around here." 
bme66feature:
  - image_path: assets/images/BME66.jpg
    alt: "BME66 image header for BME66 feature category."
    title: "BME66 &#124; Engineering Design"
    excerpt: "Here is linked all of my assignments, designs, and project updates for BME66 Engineering Design"
~~~
I'm able to make a landing page that uses some cool images (that I've credited with alt-text) to make a big title splash and associated feature rows that path to specific categories. More updates to come!