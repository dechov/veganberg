
# Veganberg

A gutenberg block that embeds a [Vega](http://vega.github.io/vega) (or [Vega-Lite](https://vega.github.io/vega-lite/)) graphic. Assumes Vega unless Vega-Lite schema indicated in the spec (`"$schema": "https://vega.github.io/schema/vega-lite/v2.json"`)

(Used https://github.com/mkaz/gutenpride as starter kit.)

### Basic testing instructions

- If you don't have a WordPress test install: [poopy.life/create](poopy.life/create), open new instance, close "Brought you by Oxygen" banner
- If you don't have Gutenberg: Plugins -> Add New, search for, install, and activate "Gutenberg"
- Upload Plugin -> choose [zip](https://github.com/dechov/veganberg/archive/master.zip), and activate
- Posts -> Add New
- Insert Vega block
- Paste spec
- Publish and view post

### Example vega spec

```json
{
  "$schema": "https://vega.github.io/schema/vega-lite/v2.json",
  "data": {"url": "https://vega.github.io/vega-lite/data/cars.json"},
  "selection": {
    "grid": {
      "type": "interval", "bind": "scales"
    }
  },
  "mark": "circle",
  "encoding": {
    "x": {
      "field": "Horsepower", "type": "quantitative",
      "scale": {"domain": [75, 150]}
    },
    "y": {
      "field": "Miles_per_Gallon", "type": "quantitative",
      "scale": {"domain": [20, 40]}
    },
    "size": {"field": "Cylinders", "type": "quantitative"}
  }
}
```
(from: https://vega.github.io/vega-lite/examples/selection_translate_scatterplot_drag.html)

![veganberg-example.png](veganberg-example.png)


### Todo

- Transform to and from core/image block
- Transform from paste, matching Vega or Vega-Lite schema
- "renderer" attribute (svg or canvas)
- "align" attribute
- Size attributes
- Support spec URL instead of only JSON
- Support externally setting Vega signals
- Codemirror for JSON editing?
