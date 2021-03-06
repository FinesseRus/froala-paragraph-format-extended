# [Froala Editor](http://github.com/froala/wysiwyg-editor/) Paragraph Format Extended plugin

[![npm](https://img.shields.io/npm/v/froala-editor-paragraph-format-extended-plugin.svg)](https://www.npmjs.com/package/froala-editor-paragraph-format-extended-plugin)
![Supported Froala Editor versions](https://img.shields.io/badge/Froala_Editor-v3-brightgreen.svg)
[![Gzip size](https://badgen.net/bundlephobia/minzip/froala-editor-paragraph-format-extended-plugin?color=green)](https://bundlephobia.com/result?p=froala-editor-paragraph-format-extended-plugin)

A plugin for Froala WYSIWYG Editor v3 that allows to choose paragraph format (tag name, 
class, etc.) from a list. It is like a mixture of the `paragraphFormat` and the `paragraphStyle` plugins with some 
extended features.

If you need a plugin for Froala Editor v2, use [version 0.1](http://github.com/Finesse/froala-editor-paragraph-format-extended-plugin/tree/froala-v2).
It won't get new features.


## Status

[![Build Status](https://travis-ci.org/Finesse/froala-editor-paragraph-format-extended-plugin.svg?branch=master)](https://travis-ci.org/Finesse/froala-editor-paragraph-format-extended-plugin)
[![dependencies Status](https://david-dm.org/Finesse/froala-editor-paragraph-format-extended-plugin/status.svg)](https://david-dm.org/Finesse/froala-editor-paragraph-format-extended-plugin)
[![devDependencies Status](https://david-dm.org/Finesse/froala-editor-paragraph-format-extended-plugin/dev-status.svg)](https://david-dm.org/Finesse/froala-editor-paragraph-format-extended-plugin?type=dev)
[![peerDependencies Status](https://david-dm.org/Finesse/froala-editor-paragraph-format-extended-plugin/peer-status.svg)](https://david-dm.org/Finesse/froala-editor-paragraph-format-extended-plugin?type=peer)


## Installation

There are several ways to install the plugin:

<details open>
<summary>Simple</summary>

Download the [plugin script](dist/paragraph_format_extended.umd.min.js) and import it using a `<script>` tag after the 
Froala Editor import.

```html
<!-- Froala Editor required stuff -->
<link href="//cdn.jsdelivr.net/npm/froala-editor@3.0/css/froala_editor.css" rel="stylesheet" type="text/css" />
<link href="//cdn.jsdelivr.net/npm/froala-editor@3.0/css/froala_style.css" rel="stylesheet" type="text/css" />
<script src="//cdn.jsdelivr.net/npm/froala-editor@3.0/js/froala_editor.min.js"></script>

<!-- Paragraph Format Extended plugin -->
<script src="//cdn.jsdelivr.net/npm/froala-editor-paragraph-format-extended-plugin@0.2/dist/paragraph_format_extended.umd.min.js"></script>
```
</details>

<details>
<summary>AMD/RequireJS</summary>

The script requires the following AMD modules to be available:

* `froala-editor` — the Froala Editor main script.

Installation:

```js
require.config({
  paths: {
    'froala-editor': '//cdn.jsdelivr.net/npm/froala-editor@3.0/js/froala_editor.min',
    'froala-editor-paragraph-format-extended-plugin': '//cdn.jsdelivr.net/npm/froala-editor-paragraph-format-extended-plugin@0.2/dist/paragraph_format_extended.umd.min'
  }
});

define('myModule', ['froala-editor', 'froala-editor-paragraph-format-extended-plugin'], function (FroalaEditor) {
  // ...
});
```

You can find more information about installation of Froala Editor using AMD in [the editor readme](http://github.com/froala/wysiwyg-editor#load-from-cdn-as-an-amd-module).
</details>

<details>
<summary>Node.js/NPM/Yarn/Webpack/Rollup/Browserify</summary>

Install the plugin:

```bash
npm install froala-editor-paragraph-format-extended-plugin --save
```

Require it:

```js
const FroalaEditor = require('froala-editor');
require('froala-editor-paragraph-format-extended-plugin');
```
</details>

## Basic usage

Create an editor, add a `paragraphFormatExtended` button to the toolbar and set up the formats list:

```html
<div id="editor"></div>
```
```js
new FroalaEditor({
  toolbarButtons: [/* Other your buttons... */ 'paragraphFormatExtended'],
  paragraphFormatExtended: [
    {title: 'Normal'},
    {tag: 'h1', title: 'Heading 1'},
    {tag: 'h2', title: 'Heading 2'},
    {tag: 'h2', 'class': 'fr-text-bordered', title: 'Header 2 bordered'},
    {tag: 'pre', id: 'code', title: 'Code'}
  ]    
});
```

## Reference

The name of the toolbar button of this plugin is `paragraphFormatExtended`.

When a paragraph format is changed by the user via the dropdown, the `class` and `id` attributes of the selected 
paragraphs are purged and replaced with the chosen format values even if they are not set.

### Options

#### paragraphFormatExtended

**Type**: `Array`

**Default value:**

```js
[
  {title: 'Normal'},
  {tag: 'h1', title: 'Heading 1'},
  {tag: 'h2', title: 'Heading 2'},
  {tag: 'h3', title: 'Heading 3'},
  {tag: 'h4', title: 'Heading 4'},
  {tag: 'h4', 'class': 'fr-text-bordered', title: 'Header 4 bordered'},
  {tag: 'pre', title: 'Code'}
]
```

A list with the formats that will appear in the Paragraph Format Extended dropdown from the toolbar. Array items are 
objects with the following attributes:

* `title` (String, required) — Format title that is shown in the dropdown. It is [translated by Froala Editor](http://froala.com/wysiwyg-editor/docs/methods#language.translate) before displaying.
* `tag` (String|Null) — Paragraph tag name. If `null` or nothing is provided the default editor tag is used.
* `class` (String|Null) — Paragraph CSS class name. May contain multiple classes devided by space.
* `id` (String|Null) — The value of paragraph `id` HTML attribute.

#### paragraphFormatExtendedSelection

**Type**: `Boolean`

**Default value:** `false`

Should the Paragraph Format Extended button from the toolbar be replaced with a dropdown showing the actual paragraph format name for the current text selection.

### Building

The source code is located in the `src` directory. Do the following to modify and compile it:

1. Install [node.js](https://nodejs.org/) version 8 or greater.
2. Open a console, go to the project root directory and run `npm install`.
3. Run `npm run build` to compile distribution files from the source files.

### Testing

Build the source code, open the [index.html](index.html) file in a browser and test it manually.

Rebuild the source code and reload the browser page manually when you change the source code. 


## Versions compatibility

The project follows the [Semantic Versioning](http://semver.org).


## License

This package is available under MIT License. However, in order to use Froala WYSIWYG HTML Editor plugin you should purchase a license for it.

See https://froala.com/wysiwyg-editor/pricing for licensing the Froala Editor.
