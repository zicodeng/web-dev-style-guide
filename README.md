# Coding Standards

## General
* Indentation
	* Use **Tab** as indentation
	* Please go to your text editor setting and change **Tab Type** to **Hard** and **Tab Length** to **4**
	
* File Naming Convention
	* Use lowercase for naming files
	* If some file names are auto-generated by some plugins or packages, do not modify them
	* For example: ` class-name `, `class`, `my-file`
	
* Comments
	* If it is a description, the first letter of the first word should be uppercase, and the rest should all be lowercase
		* For example: `This project is about ...`
	* If it is a title, the first letter of each word should be uppercase
		* For example: `About Us Section`
	
* External Resources
	* Use full path for external resources
	* For example: `background-image: url("http://www.google.com/images/example");` 
	
## HTML
* Use fewer non-semantic elements such as `div`

* Use more semantic elements such as `section`, `article`, `header`, `footer`, `nav`, `aside`, `figure`, `figcaption`
	* Why?
		* Semantic elements clearly describe meanings to both browsers and developers
		* Make search engine easier to identity the correct web page content
	
* Class or ID?
	* Use class for CSS purpose
	* Use the only id for JavaScript hook purpose
	
* Attribute Order
	* id, class, name, data-xxx, src/for/type/href, title/alt, aria-xxx, role
	* For example: `<a id="..." class="..." data-modal="toggle" href="###"></a>`
	
* Attribute Naming Convention
	* Use hyphen "-" to separate words
	
* Quotation
	* Use double quotes for outer quotes
	* Use single quotes for inner quotes
	* All attributes must be quoted
	* For example: `<input type="text" name="email" disabled="disabled" />`

* SEO
	```
	<head>
		<meta charset="utf-8">
		<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
		<!-- SEO -->
		<title>Style Guide</title>
		<meta name="keywords" content="your keywords">
		<meta name="description" content="your description">
		<meta name="author" content="author,email address">
	</head>
	```
	
* Viewport
	`<meta name="viewport" content="width=device-width, initial-scale=1.0">`
	
## CSS
* Multiple CSS selector
	* Put multiple selector in separate line
	* For example:
	```
	/* Recommended */
	.selector,
	.selector-secondary,
	.selector[type="text"] {
		padding: 15px;
 		margin-bottom: 15px;
		background-color: rgba(0,0,0,.5);
		box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
	}
	
	/*  Not recommended  */
	.selector, .selector-secondary, .selector[type=text] {
		padding:15px;
		margin:0px 0px 15px;
		background-color:rgba(0, 0, 0, 0.5);
		box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF
	}
	```

* Attribute Order
	* Positioning, box model, typography, visual, other
	* For example:
	```
	.declaration-order {
		/* Positioning */
		position: absolute;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
		z-index: 100;

		/* Box model */
		display: block;
		box-sizing: border-box;
		width: 100px;
		height: 100px;
		padding: 10px;
		border: 1px solid #e5e5e5;
		border-radius: 3px;
		margin: 10px;
		float: right;
		overflow: hidden;

		/* Typographic */
		font: normal 13px "Helvetica Neue", sans-serif;
		line-height: 1.5;
		text-align: center;

		/* Visual */
		background-color: #f5f5f5;
		color: #fff;
		opacity: .8;

		/* Other */
		cursor: pointer;
	}
	```
	
* Media Query
	* Position them right below relevant elements. Do not put all of them in one file or at buttom of css file
	
* Do Not Use `@import` in CSS

* Avoid Over-nesting
	* Keep nesting level under 3

## JavaScript
* Variable
	* Use camel case to name all variable such as `myVarName`
	
* Constant
	* use all uppercase to name all constants such as `MY_CONSTANT`
	
## PHP
* Single and Double Quotes
	* If you are evaluating something in the string, use double quotes
		* For example: `echo "<a href='$link' title='$linktitle'>$linkname</a>";`
	* If you are not evaluating anything in the string, use single quotes
		* For example: `echo '<a href="/static/link" title="Yeah yeah!">Link name</a>';`
	* You should almost never have to escape quotes in a string, because you can just alternate your quoting style
	* Dynamic text that goes into HTML attributes should be run through `esc_attr()` for security reasons
	
* Inline Code
	* Make sure to include semi-colon at the end
	* For example: `<p><?php echo "Hello World"; ?></p>`
	
* Block Code
	* Put `<?php` and `?>` tags in its own line
	* Closing PHP blocks should match the same indentation level as the opening block
	* Do not indent its containing code
	* For example:
	```
	<!-- Recommended -->
	<?php
	if(condition) {
		statement;
	}
	?>
	
	<!-- Not Recommended -->
	<?php
		if(condition) {
			statement;
		} ?>
	```
	
* Use `elseif` not `else if`

* Space Usage
	* Always put spaces after commas, and on both sides of logical, comparison, string and assignment operators
		* For example:
		```
		x == 23
		foo && bar
		! foo
		array( 1, 2, 3 )
		$baz . '-5'
		$term .= 'X'
		```
	* Put spaces on both sides of the opening and closing parenthesis of `if`, `elseif`, `foreach`, `for`, and `switch` blocks
		* For example: `foreach ( $foo as $bar ) { ...` 
	* When defining a function
		* For example: `function my_function( $param1 = 'foo', $param2 = 'bar' ) { ...`
	* When calling a function
		* For example: `my_function( $param1, func_param( $param2 ) );`
	* When performing logical comparisons
		* For example: `if ( ! $foo ) { ...`
	* When type casting
		* For example:
		```
		foreach ( (array) $foo as $bar ) { ...
		$foo = (boolean) $bar;
		```
	* When referring to array items, only include a space around the index if it is a variable
		* For example: 
		```
		$x = $foo['bar']; // correct
		$x = $foo[ 'bar' ]; // incorrect

		$x = $foo[0]; // correct
		$x = $foo[ 0 ]; // incorrect

		$x = $foo[ $bar ]; // correct
		$x = $foo[$bar]; // incorrect
		```
		
* Naming Conventions
	* Use lowercase letters in variable, action, and function names (never `camelCase`). Separate words via underscores. Don’t  		  abbreviate variable names unnecessarily; let the code be unambiguous and self-documenting
		* For example: `function some_name( $some_variable ) { [...] }`
	* Class names should use capitalized words separated by underscores. Any acronyms should be all upper case
		* For example:
		```
		class Walker_Category extends Walker { [...] }
		class WP_HTTP { [...] }
		```
	* Constants should be in all upper-case with underscores separating words
	* Files should be named descriptively using lowercase letters. Hyphens should separate words
	
* Yoda Conditions
	* When doing logical comparisons involving variables, always put the variable on the right side and put constants, literals, or 	  function calls on the left side. If neither side is a variable, the order is not important
	* For example:
	```
	if ( true == $the_force ) {
	    $victorious = you_will( $be );
	}
	```
	
* Credits
	* wordpress.org
	
## React.js
* Component Name
	* Use `MyComponent` for naming a React component (similiar to Java class name)
