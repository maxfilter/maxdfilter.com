---
title:      Making this Website
date:       2020-07-23
location:   Blacksburg, VA
---

The World Wide Web and every site on it is made of files that link to other files. These files are stored on computers around the world, which are themselves connected to create the Internet.

At first glance this might sound boring, but think about it this way: In the moments between you clicking a link and that website appearing on your screen, your computer has to find the files necessary for showing that website. To do that, it sends a message out into the Internet. At any given instant this message might be traveling at 60% the speed of light, moving under New York City, crossing through cables under the ocean and passing through the [jaws of a shark](https://slate.com/technology/2014/08/shark-attacks-threaten-google-s-undersea-internet-cables-video.html){:target="_blank"}, until it finds the files it's looking for or dies trying. Once the computer that stores those files receives a request, it sends them back to you and the website is displayed.

## Tools

So that's pretty cool, but what kind of files are used to render a web page?

First is [HTML](https://www.w3schools.com/html/default.asp){:target="_blank"} (Hypertext Markup Language), which has the actual content of the page including the titles, paragraphs and image placeholders as well as some general data about the site, like the author or links to styles and fonts. Each page on a website has an HTML file associated with it.

Next, [CSS](https://www.w3schools.com/css/default.asp){:target="_blank"} (Cascading Style Sheets) is where you add in the styles that make websites unique. For most sites you only need one CSS file, and if you've ever seen a website load weird and look like a bunch of text with blue links, that's what websites would look like without CSS.

There are some other languages you can use for styling, such as [SASS](https://sass-lang.com/){:target="_blank"} (Syntactically Awesome Style Sheets) which is basically CSS with some cool extra features that make it more compact.

Finally, if you want your website to be interactive or connect to a database, you can add in [Javascript](https://www.w3schools.com/js/js_intro.asp){:target="_blank"}. 

## Structure

This website is made with [Jekyll](https://jekyllrb.com){:target="_blank"}, which is a static site generator. The idea behind it is that instead of tediously writing out each HTML file, you create layouts that each type of post follows, like for the writing or photos sections. Jekyll will then generate the HTML from easier-to-work-with [Markdown](https://www.markdownguide.org){:target="_blank"} according to the specified layout.

Some other neat things about Jekyll are that you can write small pieces of HTML that can then be included in the different layouts, it has support for SASS and it lets you use Liquid syntax that gives you the ability to write HTML loops for adding the link of each post in an archive, for example.

That said, this is what the file structure looks like for my website:

``` bash
.
├── Gemfile
├── Gemfile.lock
├── _config.yml
├── _includes
│   ├── footer.html
│   ├── head.html
│   └── header.html
├── _layouts
│   ├── archive.html
│   ├── default.html
│   ├── photo.html
│   └── post.html
├── _photos
│   └── photo.md
├── _reading
│   └── book.md
├── _sass
│   ├── reset.sass
│   ├── typography
│   │   ├── settings.sass
│   │   └── type.sass
│   └── variables.sass
├── _writing
│   └── post.md
├── about.md
├── assets
│   ├── css
│   │   └── main.sass
│   └── images
│       ├── photos
│       │   └── photo
│       │       ├── photo-sm.jpg
│       │       └── photo.jpg
│       └── writing
├── photos.html
├── reading.html
└── writing.html
```

It looks like a lot, but it's not nearly as bad as it might seem.

## Typography & Styling

I implemented Manuel Moreale's typography layout, which he explains nicely in [this post](https://manuelmoreale.com/typography-and-spacing-in-css){:target="_blank"}.

The other styling files are `reset.sass`, which removes the style inconsistencies from each browser, `variables.sass` which has the main site variables (like font family, background color, content width...) and `main.sass`, which has the rest of the styling in the website. Jekyll takes all of this and creates a main.css file, which is stored in `./assets/css`.

## Photos

In the past, photos made my website very slow so my goal this time around was to streamline this part. My `./assets/images` folder sorts images by the post category, which currently is photos, reading, and writing. The next folder is the title of the post and stores two different photo sizes, small (512px width) and regular (2048px width). I use the small photos for the [photo grid](https://maxfilt.com/photos){:target="_blank"} (`photos.html`), and the regular ones when they are displayed [individually](https://maxfilt.com/photos/bastiments){:target="_blank"} (`./_layouts/photo.html`). Each photo is also compressed using [ImageOptim](https://imageoptim.com/mac){:target="_blank"} to make the file sizes even smaller.

Once they've been added to the assets folder, I create a new post in the `./_photos` folder, which specifies information about the photo like the `name`, `date`, `location`, and a short `description`.

## Writing & Reading

The writing and reading sections use the same archive.html layout and show all of the content in the `./_reading` and `./_writing` folders. Each writing post stores the post title, date, and location, and the reading posts also store the book's author, with each individual post (like this one) using the post.html layout.

Everything else about this website like the `Gemfile` and the `_config.yml` is standard across all Jekyll sites, so that's all there is to it really. If you're curious about the actual code for my site, you can find the most up-to-date version [here](https://github.com/maxfilter/maxfilt-com){:target="_blank"}.

If you're still here, thanks for sticking around and I hope you found this interesting.
