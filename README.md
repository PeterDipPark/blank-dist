# Blank Editor

JavaScript Plain Text Editor for Browser.

## Installation

```html
<script type="text/javascript" src="be.js"></script>
```

## Usage

Generally, you need some DOM Element for the Editor.

```html
<div id="editor"></div>
```

Attach the Editor to DOM Element

```js
be.create({
	// Editor instance ID to be used for localStorage. If the time attribute is used, there will be also '{id}_t' key for elapsed time.
	id: "blankeditor"
	// Editor DOM element.
	,element: document.getElementById('editor')
	// Initial HTML string. If not a string (i.e. false or null), content will be pulled from localStorage if available.
	,content: null
	// Callback Method.
	,callback: function(o) { console.info(o); }
	// Callback scope. If not set or false Editor object will be the scope.
	,scope: false																		
	// Editor attributes.
	,attributes: "{\"placeholder\":\"Type some text\u2026\",\"time\":0,\"words\":0,\"paste\":true,\"focus\":true}"
});
```


## Options

To temporarily block any input and stop the timer (if used) call:

```js 
be.pause() 
```

To resume, allow input again call:

```js 
be.play() 
```

To remove localStorage {id} and {id}_t key and reload window call:

```js 
be.reset() 
```

To destroy the editor and set html to DOM Element call:

```js 
be.stop() 
```

The version and build of the Editor is available at:
```js 
be.version
```

## Attributes

Editor behaviour can be altered using following attributes:

```js
{
	// Text to display when there is no content.
	placeholder: ""
	// Time limit (sec) for the Editor instance. When set to zero, there is no limit.
	,time: 0
	// Maximum words Editor can accept. When set to zero, there is no limit.
	,words: 0
	// Accept or Deny paste and drop event.
	,paste: true
	// Steal window focus on document mouseup/touchend event.
	,focus: false
}
```

## Callback

Editor will send an object with following properties to callback method on every meaningful interaction:

```js
function(o)  {
	// New HTML - dispatched on document change (default)
	if (o.html !== undefined) {
		...
	}
	// Words count - dispatched on word count change (default)
	if (o.words !== undefined) {
		...
	}
	// Words limit reached - dispatched when word limit reached (only if words attribute is -gt 0)
	if (o.wordout === true) {
		// e.g.: call be.stop() to destroy the editor
		...
	}
	// Elapsed Time in Seconds  - dispatched when time change (only if time attribute is -gt 0)
	if (o.time !== undefined) {
		...
	}	
	// Time limit reached - dispatched when time limit reached (only if time attribute is -gt 0)
	if (o.timeout === true) {
		// e.g.: call be.stop() to destroy the editor
		...
	}
	// Paste/Drop attempt - dispatched when paste attempted (only if paste attribute is false)
	if (o.paste === true) {
		...
	}
}
```

## License 
MIT

