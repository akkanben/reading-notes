# Reading Notes #12 - Chart.js, Canvas

## Chart.js

Chart.js is a JavaScript library for drawing charts. There are currently 8 types of charts.

- Line Chart
- Bar Chart
- Radar Chart
- Doughnut and Pie Charts
- Polar Area Chart
- Bubble Chart
- Scatter Chart
- Area Chart

Chart.js uses a `<canvas>` element to draw to and there are many methods to use to create the various types of charts. After declaring a canvas context a new Chart object can be instantiated with a chart type and data. Many aspects of the charts can be customized with many options.

Example from [wegbdesignerdepot.com](https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/)

```javascript
var buyerData = {
	labels : ["January","February","March","April","May","June"],
	datasets : [
		{
			fillColor : "rgba(172,194,132,0.4)",
			strokeColor : "#ACC26D",
			pointColor : "#fff",
			pointStrokeColor : "#9DB86D",
			data : [203,156,99,251,305,247]
		}
	]
}
var buyers = document.getElementById('buyers').getContext('2d');
new Chart(buyers).Line(buyerData);
```


## HTML Canvas

The `<canvas>` element can be used to draw 2d and 3d content. Like other elements that rely on JavaScript it's a good idea to add fall back content in case the canvas doesn't render in their browser. To setup the canvas a context has to be declared so the browser knows what kind of content will be drawn. 2d work can be created with `let cxt = canvas.getContext('2d')`. After the context has been declared various methods can be used to draw to the context.

- `ctx.fillRect(x, y, width, height)`
- `ctx.strokeRect(x, y, width, height)`
- `ctx.clearRect(x, y, width, height)`
- `ctx.beginPath()`
- `ctx.closePath()`
- `ctx.stroke()`
- `ctx.fill()`
- `ctx.moveTo(x, y)`
- `ctx.lineTo(x, y)`
- `ctx.arc(x, y, radius, startAngle, endAngle, counterclockwise)`
- `ctx.arcTo(x1, y1, y2, radius)`
- `ctx.quadraticCurveTo(cp1x, cp1y, x, y)`
- `ctx.bezierCurveTo(cp1x, cp1y, cp2y, x, y)`

A rainbow example:
```javascript
//color adjustments
const classicRainbow = ['red', 'orange', 'yellow', 'green', 'blue', 'purple'];
const bgColor = 'cyan';

//rainbow color thickness
const segmentWidth = 30;

const canvas = document.querySelector('canvas');
if (canvas && canvas.getContext) {
  canvas.width = 800;
  canvas.height = 350;

  const ctx = canvas.getContext('2d');
  if (ctx) {
    ctx.fillStyle = bgColor;
    ctx.lineWidth = segmentWidth;
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    let offset = segmentWidth;
    for (let segment of classicRainbow) {
      ctx.strokeStyle = segment;
      ctx.beginPath();
      ctx.arc(
        canvas.width / 2,
        canvas.height * 2 + offset,
        canvas.height * 2,
        0,
        Math.PI,
        true
      );
      ctx.stroke();
      offset += segmentWidth;
    }
  }
}
```

Colors can be added to strokes and fills using normal CSS color options like hex, rgb, rgba, hsl, hsla or color word. Colors can be blended with gradient and stroked lines can be styled with a number looks.

Line Styles:

- `lineWidth = value`
- `lineCap= value`
- `lineJoin= value`
- `miterLimit = value`
- `getLineDash()`
- `setLineDash(secments)`
- `lineDashOffset = value`

Line Caps:

- `lineCap = 'butt'`
- `lineCap = 'round'`
- `lineCap = 'square'`

Line Joins:

- `lineJoin= 'round'`
- `lineJoin= 'bevel'`
- `lineJoin= 'miter'`

Gradients:

- `createLinearGradient(x1, y1, x2, y2)`
- `createRadialGradient(x1, y1, r1, x2, y2, r2)`
- `createConicGradient(angle, x, y)`
- `gradient.addColorStop(position, color)`

Shadows:
- `shadowOffsetX = float`
- `shadowOffsetY = float`
- `shadowBlur = float`
- `shadowColor = color`


When filling with canvas there are two values that determine what gets filled with shapes intersect: "nonzero" and "evenodd".

Text:

- `fillText(text, x, y [, maxWidth])`
- `strokeText(text, x, y [, maxWidth])`
- `font = value`
- `textAlign = value`
- `textBaseline = value`
- `direction = value`
