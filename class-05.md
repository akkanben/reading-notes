# Reading Notes 05: HTML Images; CSS Color and Text

## Images

Use the `<img>` tag to place images on the HTML page. There are a few attribues to use for customizing the way the image is displayed. The `src` attribue controls which actual image file is used, whether local or external. The `alt` attribue acts as placeholder text for the image if it can not be seen, this is especially crucial for tools like screen readers. The `title` attribue provides etra information that the browser can show if the user hovers over the image with a mouse. 

The size can also be specified directly with the `height` and `width` attribues. The `<img>` tag is an inline element.

```
<article>
  <img src="images/dahlia02.jpg" alt="A photo of a single orange dahlia flower." 
    title="An orange dahlia from my garden." height="450" width="600">
  <p>Hey check out my dahlia plant it ...</p>
</article>
```

Formats:
- `.jpg` Jpg is a great compression for images that have many colors especially with smooth textures.
- `.gif` Gif is a great choice for fewer or blocks of color without gradient. Gif also has the option to display as an animation it supports limited transparency.
- `.png` Png is similar to gif as far as use cases and was designed to be a replacement for it. Png has better compression sizes than gif and also supports transparency plus a numver of other options.
- `.svg` Svgs are images created with XML using math to construct curves and plot shapes, because of this svg files are infinitly scalable without loosing sharpness.

The tags `<figure>` and `<figcaption>` are a great way to tie an image and text together semantically.

## Color

There are two main properties that control basic color for elements, `color` for text and `background-color` for the content box. There are a number of ways to identify a color in CSS.

- `rgb` & `rgba`
  - Mixes red, green and blue values from 0-255.
  - `rgba` uses and extra parameter for the alpha channel
  - Example `color: rgba(228, 25, 81)`
- `#` at the front of a hexadecimal value.
  - Uses three pairs of hexadecimal numbers, each pair controlling red, blue or green.
  - Optionally a fourth pair can be used to conrol alpha.
  - Example `color: #E41951`
- `hsl` & `hsla` are designed to [represent colors in a way that matches human vision](https://en.wikipedia.org/wiki/HSL_and_HSV).
  - `hsl` takes a hue, saturation, and lightness value and `hsla` adds the optional alpha.
  - Example `color: hlsa(343, 89%, 50%, 1)`
- By Name
  - There are 147 named colors to use.
  - Example `background-color: rebeccapurple`

## Text

General Typeface Categories
- Serif
  - Georgia
  - Times
  - Times New Roman
- Sans-serif
  - Arial
  - Verdana
  - Helvetica
- Monospace
  - Courier
  - Courier New
- Cursive
  - Comic Sans MS
  - Monotype Corsiva
- Fantasy
  - Impact
  - Haettenschweiler

Other typeface options include service-based options that come with reoccurring fees, or other sites like Sifr and Cufon.


### Units of Type Size

The default font size in a browser is 16pt. When using percentages or ems to change the size it is relative to this default.

12 Pixel Scale

| Pixels    | Percentages  | Ems       |
| --------: | -----------: | --------: | 
| h1 24px   | h1 200%      | h1 1.5em  |
| h2 18px   | h2 150%      | h2 1.3em  |
| h3 14px   | h3 117%      | h3 1.17em |
| body 12px | body 75%    | body 100% |
||| p 0.75em  |

16 Pixel Scale

| Pixels    | Percentages  | Ems       |
| --------: | -----------: | --------: | 
| h1 32px   | h1 200%      | h1 1.5em  |
| h2 24px   | h2 150%      | h2 1.3em  |
| h3 18px   | h3 133%      | h3 1.17em |
| body 16px | body 100%    | body 100% |
||| p 1em  |

Fonts come in a variety of formats: .eot, .woff, .ttf/.otf, .svg

### Text Properties
- `font-family`
  - Use to specify the typeface used in the content of an element.
  - A list of fonts can be used and the browser will choose the first availible option that the user has locally.
- `font-size` 
  - Ajust the text size in pt, em, % etc. 
- `@font-face` 
  - Allows keeping a copy of the font for the user to download if missing.
- `font-weight`
  - Values: normal, bold, lighter, bolder or \<1-1000\>
- `font-style`
  - Values: normal, italic, oblique, oblique \<angle\>
- `text-transform`
  - Values: uppercase, lowercase, capitalize
- `text-decoration`
  - Values: none, underline, overline, line-through, blink
- `line-height` 
- `letter-spacing` & `word-spacing`
- `text-align`
  - Values: left, right, center, justify
- `vertical-align` usefull for aligning text against inline elements (like `<img>`)
- `text-indent`
- `text-shadow`
  - 3 values in order: left/right length, up/down length, blur value, color
  - Blur is optional.
#### Selectors  

Other Selectors For Text
- `:first-letter` & `:first-line`
- `:link` & `:visited`
- `:hover`
- `:active`
- `:focus`

Attribute Selectors
- `[]` existance e.g. `p[class]`
- `[=]` equality e.g. `p[class="cat"]`
- `[~=]` space e.g. `p[class~="cat"]`
- `[^=]` prefix  e.g. `p[attr^"c"]`
- `[*=]` substring e.g. `p[attr*"ca"]`
- `[$=]` suffix e.g. `p[attr$"t"]`

