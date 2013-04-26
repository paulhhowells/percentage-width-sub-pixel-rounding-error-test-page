percentage width sub-pixel rounding error test page
===================================================

Use this HTML & CSS page to test percentage widths for sub-pixel rounding in different browsers / user agents.

Testing in recent versions of Safari 5.1.8, Firefox 19 and Opera 12.15 confirms that they not only round down (which avoids grid system columns from popping out of place) but also tend to make intelligent decisions to even out the spacing.  Please note that (within these recent non-IE browsers) the grid CSS stretches the last-child in a set of columns to fill the remaining gap.

Testing in IE7 and IE6 has shown that as expected they usually round up sub-pixel fractions. I have iteratively adjusted the percentages to avoid the grid columns from popping out of place at browser widths above 960px, and created a subset of overrides that work at widths down to 500px.  With IE6 & IE7 I have not attempted to adjust the last-child in each row of columns, and thus the length of each row will vary at different widths.

## Agenda
My motivation for these tests is the use of percentages within a responsive grid layout, and not to create a fluid grid system. (The testing will probably not be extensive enough for a fluid system).

It may be pragmatic to fix the overall width of any design for IE6 & IE7, and only vary the design’s width in response to media query breakpoints (in recent browsers). Perhaps with a fixed width design for IE7 & IE7 it would be a good idea to set the narrowest width column to be an integer.

## To Do
* add eighths
* test IE8, IE9, IE10, Chrome, older versions of Firefox, iPhone, iPad, Android

## Explanation / Interpreting test results
Open percentage-width-grid-test-page.html within the browser the CSS is to be tested against. Notice that the white horizontal rows are divided into units, each being set to a fraction (or percentage) of the full width of the row.

The first set of rows are labelled as being divided into sixteenths. Each of row in this set has the row width divided into units whose widths are a fraction with a denominator of 16. For example, the very first row is comprised of units each of which are 1/16, (or one sixteenth) wide. The second row comprises units each of which are 2/16 wide. The third row comprises units of widths, 3/16, 3/16, 3/16, 3/16 and 4/16 (which add up to 16/16).

The next set of rows are labelled and divided as twelfths, the set after that are sixths, then fifths, then fourths et cetera. Hopefully the HTML should correspond to what you see on the rendered page.

Within each unit there is text giving the units fraction, in the format numerator-denominator (e.g. 1-16). Perhaps it would have been clearer if I had used a slash / rather than a dash -. (I used the dash as it mirrors the CSS class used to give the unit it’s width).

That’s a lot of talk about fractions, so why does the test name refer to percentages? I use fractions because these are useful (to myself as a designer) in defining the grid system. However, the CSS defines the widths as percentages.

One difficulty with using percentages in a grid system is that it may be difficult for the browser to convert the percentages into pixels that would add up to 100% of the row’s width. Another is that different browsers calculate the pixel widths for each percentage in different ways. Allow me to explain:

Say the viewport is 400px wide. If that is divided into four column units, each a quarter of the width (i.e. 25%), then each unit is going to be 100px wide. But what width should each unit be if the viewport is narrowed to 398px? 398px / 4 = 99.5px.

We are now into sub-pixel territory — but the browser cannot render that 0.5 pixel, so it must round it up to 100px or down to 99px.

If each 1/4 unit is converted into 100px then the four units will not fit side by side on the same row. (4 * 100px = 400px but we only have 398px). That extra 2px (398px - 400px) will cause the last unit to drop down below the row. (It’s a bit like fitting books onto a bookshelf, if the total width of the books is wider than the bookshelf then the last book may find itself being put on the shelf below).

If each 1/4 unit is converted into 99px then the total width of the four units will be 396px and (although they all fit on the same row) there will be a gap at the end of the row.

So to interpret the results; for each row I am evaluating the ability of the CSS to fit all of the units onto the row. I would classify it as a 'failure' if the last unit were not to fit and 'fell off the end' below the row. If a gap is left at the end of the row then that is a tolerable alternative, although as you will see from the CSS I endeavour (in browsers other than IE6 / IE7) to make the last unit stretch to fill whatever space remains.  To aid identification the last unit in each row is underlined in black.

To generate the output (i.e. test results) I (repeatedly) drag the width of the browser from as narrow as it will go to as wide as it will go on my screen. My aim is to run this test within a comprehensive set of browsers on Mac, Windows, mobile phone and tablets. On mobile phones and tablets the resizing test may be limited to switching between portrait and landscape orientations. (Caveat: I did not test IE6 & IE7 below about 500px).

Although I am exploring the behaviour of different browsers on different devices, I think of these tests as testing this specific CSS and it’s ability to work well in different environments, rather than as tests of browser rendering.

				
				
				
