# $.richtext
is a jQuery UI widget rich text editor
fully customisable; ThemeRoller-ready

```javascript
$("textarea").richtext();
$("#editor").richtext({
		toolbar: [
			['Maximize'],['Source'],['Bold','Italic','Underline','Strike', '-', 'RemoveFormat'],
			'/',
			['TextColor'],['JustifyLeft','JustifyCenter','JustifyRight','JustifyBlock']
		]
		})
		.on('change', function() {
			console.log('change');
		});
});
```

```html
<head>
<script src="jquery.min.js"></script>
<script src="jquery-ui.min.js"></script>
<script src="qinoa-ui.qRichtext.js"></script>
<link rel="stylesheet" href="jquery-ui.min.css" />
<link rel="stylesheet" href="jquery-ui.richtext.css" />

</head>
<body>
This 
<div id="editor"></div>
<form>
<textarea></textarea>
</form>
</body>
```

## Underlying principles
Rich text editor was written to fulfill the need of the qinoa platform which need a  basic text editor for objects 'text' fields edition.

### Simplicity
To keep the code as small and simple as possible, the $.richtext plugin focuses on the interactions with the contentEditable, and provides the functionalities for event listening and user interactions. For all the rest, it relies on jQuery and rangy javascrit libraries. 

toolbar can be extended with aditional buttons.
Each button can be defined separately, like additional pugin.


### Applying style
There are 3 ways to apply a style over a text fragment:

1) wrap it inside a phrase tag (such as &lt;strong>, &lt;em>, &lt;ins>, &lt;del>, ...)
	no tag attribute is required (such tags imply some style change)
	the wrapping depth equals the number of applied styles
	
2) wrap it inside a block element (such as &lt;div>, &lt;p>, &lt;h1>, ...)
	such tag will cause a line-break
	several styles can be applied on the same element
	
3) wrap it inside a transparent inline element (such as &lt;span>)
	it is necessary to set the style attribute to the desired value (such tags provide no style change)
	several styles can be applied on the same element
