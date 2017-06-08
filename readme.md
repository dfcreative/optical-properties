# optical-properties [![unstable](http://badges.github.io/stability-badges/dist/unstable.svg)](http://github.com/badges/stability-badges)

Get optical params for a character, such as center of mass and area. Useful to do kerning, to normalize character size or to align vertically/horizontally.

See [demo](https://dfcreative.github.io/optical-properties).

[![npm install optical-properties](https://nodei.co/npm/optical-properties.png?mini=true)](https://npmjs.org/package/optical-properties/)

```js
const optics = require('optical-properties')

//get optical params
let props = optics('▲')

//draw normalized character
ctx.fontSize = size * props.scale
ctx.fillText('▲', x + props.x, y + props.y)

/*
{
	//optical center
	center: [.5, .65],

	//bounding box
	box: [.1, .2, .9, .8],

	//char area occupied
	area: .65,
	hullArea: .65,

	//scale
	scale: 1.05
}
*/
```

### let props = optics(character|canvas|imageData, options?)

Measures optical properties for the character, canvas or imageData based on the options.

Options:

* `size` − size of canvas to use, bigger is slower but more precise and vice-versa.
* `font` − font family to use for the character, defaults to `sans-serif`.
* `hull` − calculate params for [convex hull](https://en.wikipedia.org/wiki/Convex_hull) instead of actual character, that is better for icons or enframed shapes, default is `true`.

Returns:

* `center` − coordinates of optical center as `[cx, cy]`
* `box` − character bounding box `[left, top, right, bottom]`
* `area` − total white area, can be used to normalize characters