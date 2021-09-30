# Reading Notes #14a - CSS Transforms, Transitions, and Animations
Information from these article plus MDN articles:

- [Read this article on CSS Transforms](http://learn.shayhowe.com/advanced-html-css/css-transforms/)
- [Read this article on CSS Transitions & Animations](http://learn.shayhowe.com/advanced-html-css/transitions-animations/)
- [8 simple CSS3 transitions that will wow your users](http://www.webdesignerdepot.com/2014/05/8-simple-css3-transitions-that-will-wow-your-users)
- [6 Buttons animated](http://codepen.io/retyui/pen/ByoaXV)
- [CSS3 Animations: Keyframes](http://codepen.io/akshaychauhan/pen/oAfae)
- [404](http://codepen.io/kieranfivestars/pen/MYdQxX)
- [Pure CSS Bounce Animation](http://codepen.io/dp_lewis/pen/gCfBv)

MDN
- [MDN: Tranform](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) & [MDN: Using CSS Transforms](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transforms/Using_CSS_transforms)
- [MDN: Transition Property](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-property) & [MDN: Using CSS Transitions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)
- [MDN: Animation](https://developer.mozilla.org/en-US/docs/Web/CSS/animation) & [MDN: Using CSS Animations](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations)


## CSS Transforms

The `transform` property allows elements to change their shape by rotating, translating, skewing, and scaling the element. The change can be made immediately or based on user input like pseudo classes like `:hover`. There are many values that take the form of functions that can be applied with the `transform` property:

From MDN
```css
transform: matrix(1.0, 2.0, 3.0, 4.0, 5.0, 6.0);
transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1);
transform: perspective(17px);
transform: rotate(0.5turn);
transform: rotate3d(1, 2.0, 3.0, 10deg);
transform: rotateX(10deg);
transform: rotateY(10deg);
transform: rotateZ(10deg);
transform: translate(12px, 50%);
transform: translate3d(12px, 50%, 3em);
transform: translateX(2em);
transform: translateY(3in);
transform: translateZ(2px);
transform: scale(2, 0.5);
transform: scale3d(2.5, 1.2, 0.3);
transform: scaleX(2);
transform: scaleY(0.5);
transform: scaleZ(0.3);
transform: skew(30deg, 20deg);
transform: skewX(30deg);
transform: skewY(1.07rad);
```

The `tranform-origin` property can be useful with skewing, rotating and scaling. It takes a value like "top center" to use as the point to apply the rotation etc.

Example to rotate a div upside down using the bottom right corner as the rotation point:
```html
<!--html-->
<div>Some Text</div>
```
```css
/*css*/
div {
transform-origin: bottom right;
transform: rotate(180deg);
}
```

## CSS Transitions

The `transistion` property allows an element to change from one state to another with specified duration (or 0). Properties like color, margin, line-height, padding, transform, visibility, height can be changed a full list of transition-able/animation-able properties can be found on [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties). The `transition` property itself is a shorthand for four properties:

`transistion: <transistion-property> <transistion-duration> <transition-timing-function> <transistion-deley>`

- `transistion-property` is one of the many options mentioned above, or "all".
- `transistion-duration` is the length of the transition in seconds or milliseconds.
- `transistion-timing-function` controls an acceleration curve.
  - `transition-timing-function: ease;`
  - `transition-timing-function: ease-in;`
  - `transition-timing-function: ease-out;`
  - `transition-timing-function: ease-in-out;`
  - `transition-timing-function: step-start;`
  - `transition-timing-function: step-end;`
  - `transition-timing-function: steps(4, jump-end);`
  - `transition-timing-function: cubic-bezier(0.1, 0.7, 1.0, 0.1);`

Example from [MND](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions):

```html
<style>
a {
  color: #fff;
  background-color: #333;
  transition: all 1s ease-out;
}
a:hover,
a:focus {
  color: #333;
  background-color: #fff;
}
</style>

<nav>
  <a href="#">Home</a>
  <a href="#">About</a>
  <a href="#">Contact Us</a>
  <a href="#">Links</a>
</nav>
```

## CSS Animations

Animation allows creating more advanced translations and transitions, the `animation` property is a shorthand for:

- `animation-delay`
- `animation-direction`
- `animation-duration`
- `animation-fill-mode`
- `animation-iteration-count`
- `animation-name`
- `animation-play-state`
- `animation-timing-function`

Keyframes can be used to indicate changes in the animation.

Example from [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/animation):

```html
<div class="view_port">
  <div class="polling_message">
    Listening for dispatches
  </div>
  <div class="cylon_eye"></div>
</div>

<style>
.polling_message {
  color: white;
  float: left;
  margin-right: 2%;
}

.view_port {
  background-color: black;
  height: 25px;
  width: 100%;
  overflow: hidden;
}

.cylon_eye {
  background-color: red;
  background-image: linear-gradient(to right,
      rgba(0, 0, 0, .9) 25%,
      rgba(0, 0, 0, .1) 50%,
      rgba(0, 0, 0, .9) 75%);
  color: white;
  height: 100%;
  width: 20%;

  -webkit-animation: 4s linear 0s infinite alternate move_eye;
          animation: 4s linear 0s infinite alternate move_eye;
}

@-webkit-keyframes move_eye { from { margin-left: -20%; } to { margin-left: 100%; }  }
        @keyframes move_eye { from { margin-left: -20%; } to { margin-left: 100%; }  }

</style>
```
