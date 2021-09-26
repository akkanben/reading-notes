# Reading Notes #11 - Audio, Video, Images

## Images

Control the size of the `<img>` element with "height" and "width" properties. Images can be centered directly as a `display: block;` with `margin: 0px auto;`.

Images can also be applied directly to elements and set as the background with `background-image: url("../img/potato.png")`

- `background-repeat: `
  - `repeat;`
  - `repeat-x;`
  - `repeat-y;`
  - `no-repeat;`
- `background-attachment`
  - `fixed;`
  - `scroll;`

The `background-position: ` property controls where a non-repeating background image will be aligned, it takes two values: a horizontal position and a vertical position.

- `left top;`
- `left center;`
- `left bottom;`
- `center top;`
- `center center;`
- `center bottom;`
- `right top;`
- `right center;`
- `right bottom;`

The `background` property is a shorthand version using: color image-file attachment repeat

`background: #f7f7f7 url("../images/potato.png") no-repeat fixed center center`

Background images can be set to pseudo-classes like `:hover` and `:active` to create an interactive feel to elements on the page.

### Background Gradients


Using the `background` shorthand property a gradient can be used in first value position meant for color. The `linear-gradient()`, `radial-gradient()` and `conic-gradient()` functions are used for different types of gradients. Each of these can be repeated by prefixing "repeating" as in `repeating-radial-gradient()`. These functions take arguments to control direction and color. They can take many color arguments and the colors can have sizes defined with percentages or other units. If sizes overlap they with blend but sizing can be set to create had lines as well e.g. "red 50%, blue 50%"

Examples:
```css
.myGradient {
  background: linear-gradient(red, purple);
}
/* Direction keywords and degrees can be used too */
.anotherGradient {
  background: linear-gradient(40deg, yellow, green, pink, purple);
}
.oneMoreGradient {
  background: linear-gradient(to bottom left, yellow, green);
}
.hypnotize {
  background: repeating-radial-gradient(black 0% 5%, white 5% 10%);
}
```

> Details from the Duckett text plus more detail from [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Images/Using_CSS_gradients).

## Practical information

Search engine optimization (SEO) is a technique to make your site more visible to search engines and help your site be communicated in search results they way you prefer, ideally making the search results more accurate. Making sure the parts of your on-page properties are filled in like page name, headings, page descriptions will inform the search engines the details of the page.

Analytics tools are a useful way to see how many visitors are coming to your site and which pages they are viewing, how long they stay, where they come from etc.


## Audio and Video

With HTML5 browsers can use `<audio>` and `<video>` elements to play media. A nested `<source>` tag with a "scr" property set to the video will place media on the page with default browser controls. 

The browser's native controls will look different on each platform and they can be difficult to control with the keyboard. To solve this the "controls" attribute can be removed and custom controls can be programmed with HTML, CSS, and JavaScript. A simple HTML `<div>` can hold all the elements to create custom player. 

MDN example:
```html
<div class="player">
  <video controls>
    <source src="video/sintel-short.mp4" type="video/mp4">
    <source src="video/sintel-short.webm" type="video/webm">
    <!-- fallback content here -->
  </video>
  <div class="controls">
    <button class="play" data-icon="P" aria-label="play pause toggle"></button>
    <button class="stop" data-icon="S" aria-label="stop"></button>
    <div class="timer">
      <div></div>
      <span aria-label="timer">00:00</span>
    </div>
    <button class="rwd" data-icon="B" aria-label="rewind"></button>
    <button class="fwd" data-icon="F" aria-label="fast forward"></button>
  </div>
</div>
```

By editing the CSS and implementing JavaScript on the elements the look and feel as well as functionality including keyboard controls can be implemented.

In JavaScript the `removeAttribue('controls')` method can be used on the `<video>` element to get rid of the default controls. Various methods and properties are available from the [`HTMLMediaElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement) API that can be used with event listeners to create the player. The `<video>` or `<audio>` element can be selected from the DOM and assigned to a variable as the HTMLMediaElement.

```javascript
let media = document.querySelector('video');
media.play();
```

- `HTMLMediaElement.pause()`
- `HTMLMediaElement.play()`
- `HTMLMediaElement.setMediaKeys()`
- `HTMLMediaElement.currentTime`
- `HTMLMediaElement.duration`
- `HTMLMediaElement.timeupdate`

> From [MDN article on audio and video](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Video_and_audio_APIs)

## Flash

Flash was often used for videos, animations, and games on the web from the mid/late '90s to the mid 2010's. For various reasons including poor performance on mobile devices and security flaws, not to mention Steve Jobs' famous [Thoughts on Flash](https://web.archive.org/web/20170615060422/https://www.apple.com/hotnews/thoughts-on-flash/) in 2010 declaring no support in iOS, all brought about a switch to HTML5. Flash's end of life came at the end of 2020. Now modern browsers block flash content completely. 

> From the Duckett book and extra information from [Wikipedia](https://en.wikipedia.org/wiki/Adobe_Flash#End_of_life).
