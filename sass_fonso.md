#SASS

###Learning Objective(s)
* Students will be able to...
* use the main sass website for reference
* explain the 8 main topics of sass 
	- Preprocessing
	- Variables
	- Nesting
	- Partials
	- Import
	- Mixins
	- Inheritance
	- Operators

###Essential Question(s)

Q. What are at least two BIG DEALS you can do with SASS that you can't do with regular CSS?

A. Variables / Partials / Nesting / Import / Mixins / Inheritance / Operators

###Talking Points / Road Map
Have students break up into teams (3) and visit [http://sass-lang.com/guide](http://sass-lang.com/guide)

Assign one of the 8 topics to each team (15) minutes then share out findings.

	- Preprocessing
	- Variables
	- Nesting
	- Partials
	- Import
	- Mixins
	- Inheritance
	- Operators

#Build Sassy Art

Now do a code along for sass with the sassy-art files in this directory.

###Sassy-Art (Styling Rails Apps with SASS)

This is a sample Rails app (limited functionality -- Index action only) designed for the SASS lesson. 

You should be able to do a ```git pull``` and then a ```bundle install``` and ```rake db:seed``` to get this up and running. (If you have trouble with Mongoid, remove the Gemfile.lock and take the github reference out of the Gemfile, then re-bundle!)

As a class, we'll use SASS to style the app together and highlight some of the things you can do.

Feel free to use this app as additional Rails practice after the lesson (finish out CRUD functionality, style some views differently, etc.).

#Some key SASSY points

###Variables

```
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```


```
body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}
```

###Partials and Import

Partial Sass files contain little snippets of CSS that you include in other Sass files.Sass partials are used with the @import directive.

**Partial**

```
_partial.scss
```

**Import**

Let's say you have a couple of Sass files, _reset.scss and base.scss. We want to import _reset.scss into base.scss.

```
// _reset.scss

html,
body,
ul,
ol {
   margin: 0;
  padding: 0;
}
```

```
/* base.scss */

@import 'reset';

body {
  font-size: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```
###Nesting & Inheritance

Nesting is awesome (but can also be tricky if you haven't planned out your stylesheet, so map out your page structure first!).

You can nest rules inside of each other. If you have an ```<a>``` inside of a ```<nav>```, and you want those a's specially styled, you can do this:

```
nav {
	background-color: #ff3366;
	
	a {
		text-decoration: none;
		font-weight: bold;
	}

}
```

You can also use ```@extend``` to re-apply rules across selectors (inheritance!). 

**generic rule:**

```
.box {
	height: 100px;
	width: 100px;
}
```

**inherited elsewhere:**

```
.blue { 
	@extend .box;
	background-color: blue;
}

.green { 
	@extend .box;
	background-color: green;
}
```

###Mixins

Mixins are like functions for sass

```
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }
```

###Operators

You can create flexible layouts (fluid grids!) by embedding the math for sizing directly in your stylesheets.

```
 section {
 	width: 500px / 960px * 100%;
 	}
 	
```

In the above rule, the section will be 500px wide if the window is 960px wide, or **500/960 px** wide for other window widths.


###Fun facts

- The official SASS guide is [here](http://sass-lang.com/quide).
- ```@import``` lets you bring in other sheets (like the base stylesheet that comes with Twitter Bootstrap) or partials.
- You can also use conditionals, like ```@if``` to set styles.
- Additional operators (like ```&```) take things next-level, and let you select parent or child selectors.
- If you love SASS and want to use it on a non-Rails app, you can! [Compass](http://compass-style.org/) is your pal.
- Bootstrap and other front-end frameworks support SASS.

**source:**

[the sass guide](http://sass-lang.com/guide)

If you wanna go down the rabbit hole check out the reference

[sass reference](http://sass-lang.com/documentation/file.SASS_REFERENCE.html)


