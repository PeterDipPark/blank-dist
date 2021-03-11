# Blank Editor

JavaScript Plain Text Editor for Browser.

## Installation

```html
<script type="text/javascript" src="be.js"></script>
```

## Usage

Generally, you need some DOM Element to attach the Editor. 

```html
<div id="editor"></div>
```

Create an instance of the Editor.

```js
const editor = be.create({
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

To remove localStorage {id} and {id}_t key and force reload browser window call:

```js 
be.reload() 
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
	// New HTML
	if (o.html !== undefined) {
		...
	}
	// Words count
	if (o.words !== undefined) {
		...
	}
	// Elapsed Time in Seconds 
	if (o.time !== undefined) {
		...
	}	
	// Timer finished
	if (o.done===true) {
		...
	}
	// Paste/Drop event
	if (o.paste===true) {
		...
	}
}
```

## License 
MIT

