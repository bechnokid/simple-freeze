# simple-freeze

A very simple script that freezes animated GIFs. Inspired by [FreezeframeJS](https://github.com/ctrl-freaks/freezeframe.js/) and [Solaria's tutorial](https://solaria.neocities.org/guides/gifpausetut), this script should be a little more beginner-friendly to those who want to pause their GIFs without having to make static images for each one themselves. 

[Demo page](https://bechnokid.neocities.org/resources/tutorials/freezeframe/)

## Usage

### 1) HTML

Set "freeze" as the class name for each GIF individually...

```html
<img class="freeze" src="IMGSRC.gif">
```

...Or for the parent element.

```html
<div class="freeze">
  <img src="IMGSRC.gif">
  <img src="IMGSRC.gif">
  <img src="IMGSRC.gif">
</div>
```

Make buttons for playing and starting the GIFs.

```html
<button class="play-gif">Play GIFs</button>
<button class="stop-gif">Stop GIFs</button>
```

Or make a single button for toggling them.

```html
<button class="toggle-gif">Toggle GIFs</button>
```

Then, put the "Play/Stop GIFs" buttons or the "Toggle GIFs" button somewhere in the HTML.

You can also use all three types of buttons if you feel like it. The script will work either way.

### 2) JavaScript

Make a new JS file called `simple-freeze.js` and put the following in the head of the document.

```html
<script src="[PATH TO JS FILES]/simple-freeze.js" type="text/javascript">
```

Create an event listener that will create an instance of the `simple-freeze` class after the page loads.

```js
document.addEventListener("readystatechange", function () {
  if (document.readyState === "complete") {
    // Initialize script
    const f = new FreezeImages ();
  }
});
```

Make some event listeners that will fire when the user clicks on any of the previously mentioned buttons.

```js
document.addEventListener("readystatechange", function () {
  if (document.readyState === "complete") {
    // Initialize script
    const f = new FreezeImages ();

    // Set event listeners for all buttons
    for(const el of document.getElementsByClassName('play-gif')) {
      el.addEventListener('click', () => f.start());
    }

    for(const el of document.getElementsByClassName('stop-gif')) {
      el.addEventListener('click', () => f.stop());
    }

    for(const el of document.getElementsByClassName('toggle-gif')) {
      el.addEventListener('click', () => f.toggle());
    }
  }
});
```

## Methods

Public methods include:

* `start()` - Plays GIFs
* `stop()` - Pauses GIFs
* `toggle()` - Plays or pauses GIFs depending on their current state

## Options

```js
const f = new FreezeImages (
  {
    selector: "freeze",
    hover: true,
    noCss: true,
    smoothing: false,
  }
)
```

* `selector` (string) - The class name the that the script looks for to process images. Default: `"freeze"`.
* `hover` (boolean) - Adds `.ff-hover` class to `ff-container` to allow images to pause/play on hover. Default: `false`.
* `noCss` (boolean) - Tells the script to not add any additional CSS. Default: `false`.
* `smoothing` (boolean) - Tells the script to smoothen or keep the image's original sharpness. Default: `true`.

## Contribute

This script is not perfect by any means, so feel free to leave a pull request for review.