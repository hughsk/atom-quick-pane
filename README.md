# atom-quick-pane

[![stable](http://badges.github.io/stability-badges/dist/stable.svg)](http://github.com/badges/stability-badges)

Quick and easy pane creation for [Atom](https://atom.io/).

It was difficult finding documentation for how to set up a new pane that just required dealing with a `<div>` or custom element, and there's still the need to adhere to Atom's Model/View pattern currently. This package provides a simpler API for _one-off_ panes when that's all you need.

## Usage

[![NPM](https://nodei.co/npm/atom-quick-pane.png)](https://www.npmjs.com/package/atom-quick-pane)

### `pane(options, setup, teardown)`

All options and arguments are optional.

#### Options

* `options.title`: the title to include in the tab for the pane.
* `options.split`: either `'left'` or `'right'`.
* `options.activatePane`: A Boolean indicating whether to call Pane::activate on containing pane. Defaults to `true`.
* `options.element`: the element to use for the contents of the pane. This may be one of:
  * a string node name, e.g. `div` or `table`.
  * a function/constructor returning a new `HTMLElement`.
  * an existing `HTMLElement`.

#### `setup(err, element)`

Called when the pane is created and set up in the editor. `element` is the result of `options.element`.

#### `teardown()`

Called when the pane has been closed and needs to be cleaned up.

## Example
``` javascript
const Pane = require('atom-quick-pane')

Pane({
  element: 'div',
  title: 'Hello World!'
}, function (err, div) {
  if (err) throw err

  div.innerHTML = 'Hi there!'
}, function () {
  // clean up any event listeners or other resources here
})
```

## License

MIT, see [LICENSE.md](http://github.com/hughsk/atom-quick-pane/blob/master/LICENSE.md) for details.
