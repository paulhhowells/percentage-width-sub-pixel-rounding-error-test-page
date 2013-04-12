percentage width sub-pixel rounding error test page
===================================================

Use this HTML & CSS page to test percentage widths for sub-pixel rounding in different browsers / user agents.

Testing in recent versions of Safari 5.1.8, Firefox 19 and Opera 12.15 confirms that they not only round down (which avoids grid system columns from popping out of place) but also tend to make intelligent decisions to even out the spacing.  Please note that (within these recent non-IE browsers) the grid CSS stretches the last-child in a set of columns to fill the remaining gap.

Testing in IE7 and IE6 has shown that as expected they usually round up sub-pixel fractions. I have iteratively adjusted the percentages to avoid the grid columns from popping out of place at browser widths above 960px, and created a subset of overrides that work at widths down to 500px.  With IE6 & IE7 I have not attempted to adjust the last-child in each row of columns, and thus the length of each row will vary at different widths.

## Agenda
My motivation for these tests is the use of percentages within a responsive grid layout, and not to create a fluid grid system. (The testing will probably not be extensive enough for a fluid system).

It may be pragmatic to fix the overall width of any design for IE6 & IE7, and only vary the design’s width in response to media query breakpoints (in recent browsers). Perhaps with a fixed width design for IE7 & IE7 it would be a good idea to set the narrowest width column to be an integer.

## To Do
test IE8, IE9, IE10, Chrome, older versions of Firefox, iPhone, iPad, Android

				
				
				
