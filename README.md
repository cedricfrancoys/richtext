# $.richtext
A jQuery UI widget rich text editor; fully customisable; supports standard HTML5 browsers; jQuery UI ThemeRoller-ready.

Uses standard javascript libraries:
* jQuery (1.11.3);
* jQuery-UI (1.11.4);
* Rangy (1.3.0)

## Examples
```javascript
$("textarea").richtext();
$("#editor").richtext({
		toolbar: [
			['Bold','Italic','Underline','Strike', '-', 'RemoveFormat'],
			'/',
			['TextColor'],['JustifyLeft','JustifyCenter','JustifyRight','JustifyBlock']
		]
		})
		.on('change', function() {
			console.log($(this).richtext('value'));
		});
});
```

```html
<head>
<script src="http://code.jquery.com/jquery-1.11.3.min.js"></script>
<script src="http://code.jquery.com/ui/1.11.4/jquery-ui.min.js"></script>
<script src="js/qinoa-ui.qRichtext.js"></script>
<link rel="stylesheet" href="http://code.jquery.com/ui/1.11.4/themes/smoothness/jquery-ui.css" />
<link rel="stylesheet" href="css/jquery-ui.richtext.css" />

</head>
<body>
    <div id="editor"></div>
    <form>
        <div>
        <label for="text">Text:</label><textarea name="text">Lorem ipsum sit amet.</textarea>
        </div>
    </form>
</body>
```

## Quick presentation
To keep the code as small and simple as possible, the $.richtext plugin focuses on the interactions with the contentEditable, and provides the functionalities for event listening and user interactions. For all the rest, it relies on jQuery and Rangy javascript libraries. 

Toolbar can be extended with aditional buttons.
Each button can be defined separately, like additional pugin.

## Inner logic
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
