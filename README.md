<<<<<<< HEAD

# dgmd story-telling project
This site was a very personal project built around media and content that was important to me.  While you are welcome and encouraged to build _anything you’d like_ as your first, story-telling project, we are sharing this project with all of you to serve as a code base and framework for beginning to mess around with HTML, CSS, Javascript, and story-telling.  The extensions outlined below are meant to acquaint you with the project and offer you some challenges and guidance in trying to adapt and extend this project into a story of your own.

As with anything in this course, if you have any questions, please [let us know](mailto:dgmde15@gmail.com) earlier rather than later, so we can help get you coding.  

## Extension 1 :: Change Background Image & Content
=======
# DGMD E-15 — Storytelling Project

[This site](http://dgmd.github.io/a-story-in-pomes) was a very personal project built around media and content that was important to me.  While you are welcome and encouraged to build _anything you’d like_ in this course, we are sharing this project with all of you to serve as a code base and framework for beginning to mess around with HTML, CSS, Javascript, and story-telling.  The extensions outlined below are meant to acquaint you with the project and offer you some challenges and guidance in trying to adapt and extend this project into a story of your own.  

In addition, you'll notice that the "Master" branch of this repository is empty except for this README.  This is because the site is being served with GitHub Pages.  In order to host a site from a GitHub repository, you must create a branch called gh-pages.  So switch to [the gh-pages branch](https://github.com/dgmd/a-story-in-pomes/tree/gh-pages) of this repository to see the files that went into making it.

As with anything in this course, if you have any questions, please [let us know](mailto:dgmde15@gmail.com) earlier rather than later, so we can help get you coding.  

## Extension 1 — Change Background Image & Content
>>>>>>> dgmd/master
In order to acquaint yourself with the structure of the project and to make it your own, we’d first like to challenge you to swap out all the poems, music, and pictures that reflect Shaunalynn’s story and repopulate the site with media that will tell a story _you_ care about.

If you have content that can be meaningfully geo-tagged, you might want to hold onto the map interface (What about zooming the google map into New England and making the site display your own photography?  Or a travel diary for past and future trips?)

Otherwise, you might comment out the entire map interface and add content with a totally different organization (Your nana’s recipes organized seasonally? Or maybe a digital baby book for a friend with a new child at home?)

Once you’ve come up with an idea, here are some directions on how to start bringing in your own content.

<<<<<<< HEAD
First, you should step through the full commit history in the project repository.  Each commit message includes a pretty extensive, step-by-step description of the part of the project added in that commit’s code.  

_To change background images:_  Lines 86-119 of pomes.js define which photos are cycled through as background images in the site.  In order to put in your own images, the lists <code>detroit_bgimgs</code>, <code>clifftop_bgimgs</code>, <code>la_bgimgs</code>, and <code>orlando_bgimgs</code> must contain _relative_ paths to your images.  I hosted my pictures and media on Amazon S3, so my _base_ url, defined by the variable <code>media_base_path</code>, is to my projects S3 “bucket” (You can read more [here]()).  If you host your own images somewhere else, your <code>media_base_path</code> will be different.

_To change other content:_  In pomes.html, the main content of the site is organized in this way:

<code>
=======
First, you should step through the full commit history in the project repository.  Each commit message includes a pretty extensive, step-by-step description of the part of the project added in that commit’s code.

_To change background images:_  [Lines 86-119 of `pomes.js`](https://github.com/dgmds15/a-story-in-pomes/blob/gh-pages/pomes.js#L86-119) define which photos are cycled through as background images in the site.  In order to put in your own images, the lists `detroit_bgimgs`, `clifftop_bgimgs`, `la_bgimgs`, and `orlando_bgimgs` must contain _relative_ paths to your images.  I hosted my pictures and media on Amazon S3, so my _base_ url, defined by the variable `media_base_path`, is to my projects S3 "bucket" (You can read more [here](http://www.smalldatajournalism.com/projects/one-offs/using-amazon-s3/)).  If you host your own images somewhere else, your `media_base_path` will be different.

_To change other content:_  In `pomes.html`, the main content of the site is organized in this way:

```html
>>>>>>> dgmd/master
<div class="trip">
	<h1 id="detroit"><a href="#detroit">Detroit, MI</a></h1>
	
	<div class="pome-block" id="2014-07-18-0919-DETROIT-KP">
	<h2><a href="#">one minute pomes #1</a></h2>
		<div class="pome">
			Poem Text Here
		</div>
	</div>

	<div class="pome-block" id="2014-07-19-0049-DETROIT-SD">
	<h2><a href="#">re: one minute pomes #1</a></h2>
		<div class="pome">
			Poem Text Here
		</div>
	</div>
</div>
<<<<<<< HEAD
</code>

Any text or images you want to include in entries should go in the <code>div.pome</code>, titles in the <code>h2 a</code>, and trip (or section) titles in the <code>h1</code> tags.  Make multiple <code>.trip</code>s if you want multiple sections.

**NOTE**  If you decide to change any variable, function, id, or class names in these files, you will need to make sure you change all references to them throughout the html, js, and css files so things don’t break!

## Extension 2 :: Change Formatting of Byline Dates & Times
Currently, each poem has a programmatically generated byline which gives the person and timestamp of its authorship, but it is being displayed in a somewhat obscure way using military time and numbers for dates.  We’d like to ask that you rewrite these bylines so they are more human-readable, displaying the dates as  “January 1, 2015” rather than “01.01.2015” and the time as “5:55PM” rather than “15:55”.
 
The current bylines are being generated in the function <code>generate_byline</code> on lines 223-236 in pomes.js using [Regular expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions). This function is taking the unique IDs assigned to each <code>div.pome-block</code> and reassembling them into a readable byline.  Using regular expressions — or some other approach — try to rewrite the bylines in the format listed above.

**NOTE**  If you are having trouble, remember you can write Javascript directly into the Google Chrome Console (Cmd-Opt-i).  Try to write the code line by line in the console until you get your desired effect there.  Then try to move it back into pomes.js once you have some working code.

## Extension 3 :: Fix Background Image Changing Algorithm
There is currently a "bug" in the background image code which means that, when the background changes due to a click in the navbar, a random picture is chosen every time.  This can lead to the same image being chosen multiple times consecutively, making it feel to users like there is no response to their action.  

Right now, background image changes are controlled in two places on the pomes.js file.  First, the <code>change_bgimgs</code> function, within the <code>window.onscroll</code> function changes the background images as a user scrolls.  Second, the <code>nav_onclick</code> function changes the background image when the user clicks on the navbar.  Change the <code>nav_onclick</code> function so that it chooses a random image _which is not the current background image_.

## Extension 4A :: Pull in Images Using the Flickr API
=======
```

Any text or images you want to include in entries should go in the `div.pome`, titles in the `h2 a`, and trip (or section) titles in the `h1` tags.  Make multiple `.trip`s if you want multiple sections.

**NOTE**  If you decide to change any variable, function, id, or class names in these files, you will need to make sure you change all references to them throughout the html, js, and css files so things don’t break!

### Resources for Extension 1
+ MDN's [reference page on `background`](https://developer.mozilla.org/en-US/docs/Web/CSS/background)
+ MDN's [page on the interaction between JS and CSS](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_started/JavaScript)
+ [This CodePen](http://codepen.io/aresnick/pen/JdZmMG) (note the comments) demonstrating changing a background as you scroll.

---

## Extension 2 — Change Formatting of Byline Dates & Times
Currently, each poem has a programmatically generated byline which gives the person and timestamp of its authorship, but it is being displayed in a somewhat obscure way using military time and numbers for dates.  We’d like to ask that you rewrite these bylines so they are more human-readable, displaying the dates as  "January 1, 2015" rather than 01.01.2015" and the time as "5:55PM" rather than "15:55".
 
The current bylines are being generated in the function `generate_byline` on lines 223-236 in `pomes.js` using [regular expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions). This function is taking the unique IDs assigned to each `div.pome-block` and reassembling them into a readable byline.  Using regular expressions — or some other approach — try to rewrite the bylines in the format listed above.

**NOTE**  If you are having trouble, remember you can write Javascript directly into the Google Chrome Console (Cmd-Opt-j).  Try to write the code line by line in the console until you get your desired effect there.  Then try to move it back into `pomes.js` once you have some working code.

### Resources for Extension 2

+ [This short tutorial](https://msdn.microsoft.com/library/ff743760(v=vs.94).aspx) on formatting dates and times in JavaScript
+ [MDN's reference on the Date object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

---

## Extension 3 — Fix Background Image Changing Algorithm
There is currently a "bug" in the background image code which means that, when the background changes due to a click in the navbar, a random picture is chosen every time.  This can lead to the same image being chosen multiple times consecutively, making it feel to users like there is no response to their action.  

Right now, background image changes are controlled in two places on the `pomes.js` file.  First, the `change_bgimgs` function, within the `window.onscroll` function changes the background images as a user scrolls.  Second, the `nav_onclick` function changes the background image when the user clicks on the navbar.  Change the `nav_onclick` function so that it chooses a random image _which is not the current background image_.

### Resources for Extension 3

+ [MDN's `Math.random` reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)
+ [This CodePen](http://codepen.io/aresnick/pen/oXyaKw) playing around with `background-color` via `Math.random`
+ [This StackOverflow answer](http://stackoverflow.com/questions/1527803/generating-random-numbers-in-javascript-in-a-specific-range) explaining how to generate a random number in a range.
+ ["JavaScript for Cats" on arrays](http://jsforcats.com/#arrays) and [MDN's reference on Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

---

## Extension 4A — Pull in Images Using the Flickr API
>>>>>>> dgmd/master
In Extension 1, we asked you to repopulate the site with personal content, finding a way to host it online if it wasn’t already, to tell your own story.  But, there are a lot of stories to tell that aren’t about us as individuals.  In this extension, rather than using your own content, we are going to access information from an external web source using an API (Application Program Interface).  An API allows you to get programmatic access to the contents of another site. Services like [Twitter](https://dev.twitter.com/web/javascript), [Facebook](https://developers.facebook.com/docs/javascript), [Google Maps](http://www.programmableweb.com/api/google-maps), which is used in this project, and others all have APIs you can use to access their content.

[Flickr](https://www.flickr.com/services/feeds/docs/photos_public/) has a particularly accessible API so, for this extension, we are asking that you replace the background images of the site with images already publicly available on Flickr, accessing those images through their API.

<<<<<<< HEAD
## Extension 4B :: Pull in Outside Media Using Another API 
=======
### Resources for Extension 4A

+ [This short video](https://www.youtube.com/watch?v=B9vPoCOP7oY) attempting to explain what [an API](https://en.wikipedia.org/wiki/Application_programming_interface) is.
+ [This](http://code.tutsplus.com/tutorials/the-ultimate-guide-to-decoding-the-flickr-api--net-5981) and [this](http://mashupguide.net/1.0/html/ch08s07.xhtml) on accessing the Flickr API.
+ [This summary of the JSONP technique](https://en.wikipedia.org/wiki/JSONP)
+ [This](http://www.sitepoint.com/load-flickr-photos-using-jsonapi/) tutorial on accessing the Flickr API via JSONP.
+ [The Flickr API reference](https://www.flickr.com/services/api/)

---

## Extension 4B — Pull in Outside Media Using Another API 

>>>>>>> dgmd/master
Think about a story you might be able to tell, using this project as a framework for incorporating data from another outside source.  You can check out [this list](http://www.programmableweb.com/apis/directory) to peruse some of the many web services that provide APIs that allow you programmatic access to their content.  Imagine the stories you might tell using this data:

+ What if you created a curated list of tweets from #blacklivematter actions across the nation and displayed them organized by city?  

+ If you are a photographer and already host your images on Flickr, what if you create a geo-tagged portfolio displaying the images you’ve already uploaded to Flickr?  

+ What if you created a baby book (as described in Extension 1 above) that auto-populated based on a parent’s Facebook posts about their new child?

Working with APIs is a big endeavor, especially if you are new to programming, so if you have any questions about how to use APIs or about scoping a project, please talk with one of us!  We’d be happy to help you figure out what an appropriately sized project looks like!

<<<<<<< HEAD
## Extension 5 :: Rewrite Camera Functionality with New Tokens
The current physical interface to the site uses color recognition to identify the tokens placed in front of the camera.  When a token is placed in front of the camera, its color is identified and used through the following steps:

+ accesses the built-in camera’s video output
+ captures a still image from that feed
+ accesses the pixel color data from that image
+ calculates the average color of the image
+ identifies that color by name based on its location in the RGB color space
+ uses that color name as an anchor link into the site’s content

The decision to use color recognition and the particular approach to implementing that recognition was based on a desire to have colorful tokens which could be made on the fly, using crayons or markers.  What if you wanted to use a different type of token?

For this extension we are asking that you write your own image recognition program to recognize a different type of token.  We encourage you to come up with your own ideas, but we can recommend these particular tools and libraries if you want some suggestions and guidance:

+ **text-based tokens** Check out [this OCR-based project](http://kdzwinel.github.io/JS-OCR-demo/) with available source code, high-level walk-through, and videos below. 
+ **shape-based tokens** [One](http://katspaugh.github.io/whiteboard/examples/brain/#triangle) of [these](http://techslides.com/object-detection-with-html5-getusermedia) 
+ **face-based tokens** Check out this face recognition [JS library](http://stackoverflow.com/questions/7291065/any-library-for-face-recognition-in-javascript) if you’d like your camera to recognize and respond to faces in the camera feed.
=======
---

## Extension 5 — Rewrite Camera Functionality with New Tokens
The current physical interface to the site uses color recognition to identify the tokens placed in front of the camera.  When a token is placed in front of the camera, its color is identified and used through the following steps:

1. accesses the built-in camera’s video output
2. captures a still image from that feed
3. accesses the pixel color data from that image
4. calculates the average color of the image
5. identifies that color by name based on its location in the RGB color space
6. uses that color name as an anchor link into the site’s content

The decision to use color recognition and the particular approach to implementing that recognition was based on a desire to have colorful tokens which could be made on the fly, using crayons or markers.  What if you wanted to use a different type of token?

### Resources for Extension 5

For this extension we are asking that you write your own image recognition program to recognize a different type of token.  We encourage you to come up with your own ideas, but we can recommend these particular tools and libraries if you want some suggestions and guidance:

+ **Text-based tokens** — Check out [this OCR-based project](http://kdzwinel.github.io/JS-OCR-demo/) with available source code, high-level walk-through, and videos below. 
+ **Shape-based tokens** — [One](http://katspaugh.github.io/whiteboard/examples/brain/#triangle) of [these](http://techslides.com/object-detection-with-html5-getusermedia) 
+ **Face-based tokens** — Check out this face recognition [JS library](http://stackoverflow.com/questions/7291065/any-library-for-face-recognition-in-javascript) if you’d like your camera to recognize and respond to faces in the camera feed.
>>>>>>> dgmd/master
