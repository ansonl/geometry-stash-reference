---
layout: page
title: Shape Drawing Reference
permalink: /shape-drawing-reference/
---

Create custom slides for Geometry Stash by writing your own slides files. 

A slide file is a JSON file with key value dictionary at its root. A barebones slide file is shown below. All code examples here are part of the default `#Shape Element Drawing Demo` slides preloaded by Geometry Stash. 

```json
{
  "elements": [
    /* PUT ELEMENTS HERE
  ],
  "bgcolor": "#FFFFFF",
  "title": "#Shape Element Drawing Demo",
  "author": "anson",
  "description": "A sample file that demonstrates Geometry Stash shape drawing capabilities. "
}
```

Base File
------
Key `elements` contains a dictonary of elements that are drawn. Types of elements:
  * [Line](#line)
  * [Rectangle](#rectangle)
  * [Circle](#circle)
  * [Arc](#arc)
  * [Ellipse](#ellipse)
  * [Bézier Curve](#bzier-curve) (Quadratic & Cubic)
  * [Chain](#chain)
  * [Text](#text)

Key `bgcolor` contains a string value that is a hex RGB color. The background of the slide is set to this color. 
Key `title` contains a string value of the slide display title. This is the name of the slide shown in the table view in the app. 
Key `author` contains a string value of the slide author. 
Key `description` contains a string description of the slide. 

The coordinate system of slides is similar to [HTML Canvas](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial). It is in the fourth quardrant of the [Cartesian Plane](http://www.purplemath.com/modules/plane3.htm). The X axis increase to the right and Y axis increases downwards. 
Angular measurements are in degrees, start at the 0 at the three'oclock postion and increase clock wise. 

Line
------
A `line` element draws a line from `origin` to `end`. 

```json
{
  "comment": "a sample line"
  "shapeType": "line",
  "originx": 100,
  "originy": 100,
  "thickness": 20,
  "endx": 1000,
  "endy": 600,
  "strokeColor": "#333333"
}
```

Rectangle
------
A `rectangle` element draws a rectangle at `origin` of `width` and `height`.

```json
{
  "shapeType": "rectangle",
  "originx": 1200,
  "originy": 100,
  "thickness": 50,
  "width": 800,
  "height": 800,
  "strokeColor": "#357EC7",
  "fillColor": "#FFA62F"
}
```

Circle
------
A `circle` element draws a circle at `origin` of radius `radius`.

```json
{
  "shapeType": "circle",
  "originx": 2500,
  "originy": 550,
  "thickness": 50,
  "radius": 100,
  "strokeColor": "#437C17",
  "fillColor": "#800000"
}
```

Arc
------
An `arc` element draws an arc at `origin` of radius `radius` from `startAngle` to `endAngle`. **Arc draws counter-clockwise while the angular measurement increases clockwise.**

```json
{
  "shapeType": "arc",
  "originx": 450,
  "originy": 1750,
  "thickness": 30,
  "radius": 300,
  "startAngle": 0,
  "endAngle": 160,
  "strokeColor": "#FF0000",
  "fillColor": "#56A5EC"
}
```

Ellipse
------
An `ellipse` element draws an ellipse at `origin` of `width` and `height`.

```json
{
  "shapeType": "ellipse",
  "originx": 100,
  "originy": 1000,
  "width": 500,
  "height": 200,
  "thickness":20,
  "strokeColor": "#AF9B60",
  "fillColor": "#F3E5AB"
},
```

Bézier Curve
------
A `curve` element draws a bézier curve from `origin` to `end`. It uses `controlPoint1` and `controlPoint2` to create the curve. **Absence of `controlPoint2` results in a Quadratic bézier curve.**

```json
{
  "comment": "Quadratic bézier curve",
  "shapeType": "curve",
  "originx": 1050,
  "originy": 1950,
  "thickness": 20,
  "endx": 1950,
  "endy": 1950,
  "controlPoint1x": 1500,
  "controlPoint1y": 2650,
  "strokeColor": "#FDD017",
  "fillColor": "#FF4400"
},
{
  "comment": "Cubic bézier curve",
  "shapeType": "curve",
  "originx": 1050,
  "originy": 1950,
  "thickness": 20,
  "endx": 1950,
  "endy": 1950,
  "controlPoint1x": 1250,
  "controlPoint1y": 1550,
  "controlPoint2x": 1650,
  "controlPoint2y": 2350,
  "strokeColor": "#FF4400",
  "fillColor": "#FF4400"
}
```

Chain
------
A `chain` element starts at `origin` and contains an array of elements. These elements start at the end of the preceding element in the chain array. **All elements in the chain array can omit the `origin` keys.** 

```json
{
  "shapeType": "chain",
  "originx": 2400,
  "originy": 1700,
  "elements": [
    /* PUT ELEMENTS HERE */
  ]
}
```

Text
------
A `text` element draws a textbox at `origin` of `width` and `height`. It can be made interactive by setting the `interactive` key to `true`. **Textboxs are non-interactive by default.**

```json
{
  "shapeType": "text",
  "originx": 1500,
  "originy": 2400,
  "width": 1200,
  "height": 500,
  "fontHeight": 100,
  "fillColor": "#EEEEEE",
  "bgcolor": "#222222",
  "interactive": true,
  "alignment" : "justified",
  "text": "Lorem ipsum dolor sit amet."
}
```

Putting it all together
------
The preloaded sample file

``json
{
  "elements": [
    {
      "comment": "line description",
      "shapeType": "text",
      "originx": 400,
      "originy": 50,
      "width": 500,
      "height": 200,
      "fontHeight": 150,
      "fillColor": "#000000",
      "interactive": false,
      "text": "Lines"
    },
    {
      "shapeType": "line",
      "originx": 100,
      "originy": 100,
      "thickness": 20,
      "endx": 1000,
      "endy": 600,
      "strokeColor": "#333333"
    },
    {
      "shapeType": "line",
      "originx": 100,
      "originy": 100,
      "thickness": 20,
      "endx": 900,
      "endy": 650,
      "strokeColor": "#FF0000"
    },
    {
      "shapeType": "line",
      "originx": 100,
      "originy": 100,
      "thickness": 20,
      "endx": 850,
      "endy": 700,
      "strokeColor": "#FBB917"
    },
    {
      "shapeType": "line",
      "originx": 100,
      "originy": 100,
      "thickness": 20,
      "endx": 800,
      "endy": 750,
      "strokeColor": "#FFD801"
    },
    {
      "shapeType": "line",
      "originx": 100,
      "originy": 100,
      "thickness": 20,
      "endx": 750,
      "endy": 800,
      "strokeColor": "#6AA121"
    },
    {
      "shapeType": "line",
      "originx": 100,
      "originy": 100,
      "thickness": 20,
      "endx": 700,
      "endy": 850,
      "strokeColor": "#0000A0"
    },
    {
      "comment": "rectangle description",
      "shapeType": "text",
      "originx": 1450,
      "originy": 250,
      "width": 800,
      "height": 700,
      "fontHeight": 100,
      "fillColor": "#FFFFFF",
      "interactive": true,
      "text": "Rectangles\n\n↓ Ordering\nSet which shape appears on top by changing the element order in the slide file elements array.\nText will always appear above shape elements."
    },
    {
      "shapeType": "rectangle",
      "originx": 1200,
      "originy": 100,
      "thickness": 50,
      "width": 800,
      "height": 800,
      "strokeColor": "#357EC7",
      "fillColor": "#FFA62F"
    },
    {
      "shapeType": "rectangle",
      "originx": 1300,
      "originy": 350,
      "thickness": 50,
      "width": 800,
      "height": 800,
      "strokeColor": "#2B65EC"
    },
    {
      "shapeType": "rectangle",
      "originx": 1450,
      "originy": 200,
      "thickness": 50,
      "width": 800,
      "height": 800,
      "fillColor": "#56A5EC"
    },
    {
      "comment": "arc description",
      "shapeType": "text",
      "originx": 550,
      "originy": 1800,
      "width": 800,
      "height": 200,
      "fontHeight": 150,
      "fillColor": "#000000",
      "text": "Arcs"
    },
    {
      "shapeType": "arc",
      "originx": 450,
      "originy": 1750,
      "thickness": 30,
      "radius": 300,
      "startAngle": 0,
      "endAngle": 160,
      "strokeColor": "#FF0000",
      "fillColor": "#56A5EC"
    },
    {
      "shapeType": "arc",
      "originx": 700,
      "originy": 1750,
      "thickness": 30,
      "radius": 300,
      "startAngle": 230,
      "endAngle": 45,
      "strokeColor": "#FF0000"
    },
    {
      "comment": "circle description",
      "shapeType": "text",
      "originx": 3050,
      "originy": 400,
      "width": 700,
      "height": 200,
      "fontHeight": 150,
      "fillColor": "#FF0000",
      "interactive": false,
      "text": "Circles"
    },
    {
      "shapeType": "circle",
      "originx": 2500,
      "originy": 550,
      "thickness": 50,
      "radius": 100,
      "strokeColor": "#437C17",
      "fillColor": "#800000"
    },
    {
      "comment": "ellipse description",
      "shapeType": "text",
      "originx": 100,
      "originy": 800,
      "width": 700,
      "height": 200,
      "fontHeight": 150,
      "fillColor": "#000000",
      "interactive": false,
      "text": "Ellipse"
    },
    {
      "shapeType": "circle",
      "originx": 2800,
      "originy": 550,
      "thickness": 20,
      "radius": 300,
      "fillColor": "#657383"
    },
    {
      "shapeType": "circle",
      "originx": 3250,
      "originy": 550,
      "thickness": 20,
      "radius": 400,
      "strokeColor": "#A1C935"
    },
    {
      "shapeType": "ellipse",
      "originx": 100,
      "originy": 1000,
      "width": 500,
      "height": 200,
      "thickness":20,
      "strokeColor": "#AF9B60",
      "fillColor": "#F3E5AB"
    },
    {
      "shapeType": "ellipse",
      "originx": 100,
      "originy": 1100,
      "width": 500,
      "height": 200,
      "thickness":20,
      "fillColor": "#667C26"
    },
    {
      "shapeType": "ellipse",
      "originx": 100,
      "originy": 1200,
      "width": 500,
      "height": 200,
      "thickness":20,
      "strokeColor": "#AF9B60"
    },
    {
      "comment": "curve description",
      "shapeType": "text",
      "originx": 1000,
      "originy": 1300,
      "width": 1000,
      "height": 500,
      "fontHeight": 150,
      "fillColor": "#000000",
      "interactive": true,
      "text": "↓ Bézier Curves\nQuadratic & Cubic curves"
    },
    {
      "comment": "Cubic bézier curve",
      "shapeType": "curve",
      "originx": 1050,
      "originy": 1950,
      "thickness": 20,
      "endx": 1950,
      "endy": 1950,
      "controlPoint1x": 1250,
      "controlPoint1y": 1550,
      "controlPoint2x": 1650,
      "controlPoint2y": 2350,
      "strokeColor": "#FF4400"
    },
    {
      "comment": "Cubic bézier curve",
      "shapeType": "curve",
      "originx": 950,
      "originy": 1800,
      "thickness": 20,
      "endx": 1850,
      "endy": 1800,
      "controlPoint1x": 1150,
      "controlPoint1y": 1400,
      "controlPoint2x": 1550,
      "controlPoint2y": 2200,
      "fillColor": "#FF4400"
    },
    {
      "comment": "Quadratic bézier curve",
      "shapeType": "curve",
      "originx": 1050,
      "originy": 1950,
      "thickness": 20,
      "endx": 1950,
      "endy": 1950,
      "controlPoint1x": 1500,
      "controlPoint1y": 2650,
      "strokeColor": "#FDD017"
    },
    {
      "comment": "Cubic bézier curve",
      "shapeType": "curve",
      "originx": 1300,
      "originy": 2100,
      "thickness": 40,
      "endx": 950,
      "endy": 1950,
      "controlPoint1x": 1300,
      "controlPoint1y": 2850,
      "strokeColor": "#FDD017",
      "fillColor": "#9E7BFF"
    },
    {
      "comment": "chain description",
      "shapeType": "text",
      "originx": 2200,
      "originy": 1000,
      "width": 1700,
      "height": 700,
      "fontHeight": 150,
      "fillColor": "#000000",
      "interactive": true,
      "text": "↓ Chain of elements\nYou can chain line and curve elements into single elements that start at the end of the previous element in the chain.\nThe chain below is a  line → cubic bézier curve →  line"
    },
    {
      "shapeType": "chain",
      "originx": 2400,
      "originy": 1700,
      "elements": [
        {
          "shapeType": "line",
          "thickness": 40,
          "endx": 2400,
          "endy": 2000,
          "strokeColor": "#0000AA"
        },
        {
          "shapeType": "curve",
          "thickness": 30,
          "endx": 3400,
          "endy": 2000,
          "controlPoint1x": 2600,
          "controlPoint1y": 2500,
          "controlPoint2x": 2900,
          "controlPoint2y": 1500,
          "strokeColor": "#FF8040",
          "fillColor": "#AA33AA"
        },
        {
          "shapeType": "line",
          "thickness": 40,
          "endx": 3500,
          "endy": 1800,
          "strokeColor": "#0000AA"
        }
      ]
    },
    {
      "shapeType": "text",
      "originx": 1500,
      "originy": 2400,
      "width": 1200,
      "height": 500,
      "fontHeight": 100,
      "fillColor": "#EEEEEE",
      "bgcolor": "#222222",
      "interactive": true,
      "alignment" : "justified",
      "text": "↓ Some interactive text.\nLorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
    },
    {
      "shapeType": "text",
      "originx": 2700,
      "originy": 2400,
      "width": 1200,
      "height": 500,
      "fontHeight": 100,
      "fillColor": "#000000",
      "interactive": false,
      "alignment" : "center",
      "text": "Text is non-interactive by default.\nSome non interactive text.\n Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
    },
    {
      "shapeType": "text",
      "originx": 100,
      "originy": 2050,
      "width": 1350,
      "height": 950,
      "fontHeight": 125,
      "fillColor": "#000000",
      "interactive": true,
      "alignment" : "left",
      "text": "↓ Making and sharing custom slides is easy, click 📁 to manage slides, check out documentation 📖 online at GeometryStash.com"
    }
  ],
  "bgcolor": "#FFFFFF",
  "title": "#Shape Element Drawing Demo",
  "author": "anson",
  "description": "A sample file that demonstrates Geometry Stash shape drawing capabilities. "
}
```
