# PARADOX: Gridkoo - A simple SCSS/Compass Grid plugin
This is a simple SCSS plugin to easily create grid system in your project.

## Usage

### Setting the grid

I assume your project structure is like this:
	/project-folder
		style.scss
		/partials //This is the directory of your Sass files

Copy `_grid.scss` to `partials` directory. Then import it from `style.css` using import method `@import "partials/grid";`. Then you have to setting the grid using variables like this:
	
	// Grid variable
	// ------------------
	$total-cols             : 12; //Total Columns
	$col-width              : 60px; //Column width, you can use 'em', '%' or other valid css unit as well
	$gutter-width           : 20px; //Gutter width
	$side-gutter-width      : 10px; //Side Gutter width

	$show-grid-backgrounds  : true; // Showing the grid background, change to 'false' to hide the background

### Using the grid

#### Setting Grid Container
First, set the container/wrapper of your site to center the element.

Example:
	.wrapper {
		@include container;
	}

CSS Output:
	.container {
		*zoom: 1;
		margin: auto;
		width: 960px;
	}
	.container:after {
		content: "";
		display: table;
		clear: both;
	}
#### The Grid Column
Use `columns` mixin to set the width of an element.
	Example:
		.element {
			@include columns(4);
		}

	CSS Output:
		.element {
			display: inline;
			float: left;
			margin-right: 20px;
			width: 300px;
		}

In case your element is in the first column within the parent, you'll need to use `alpha` mixin.
	Example:
		.element {
			@include columns(4);
			@include alpha;
		}

	CSS Output:
		.element {
			display: inline;
			float: left;
			margin-right: 20px;
			width: 300px;
			margin-left: 10px;
		}

Then if your element is in the last columns, use the `omega` mixin.
	Example:
		.element {
			@include columns(4);
			@include omega;
		}

	CSS Output:
		.element {
			display: inline;
			float: right;
			margin-right: 10px;
			width: 300px;
		}

### Changelog
* 	1.0.0
	Initial release