# Nomia

A Small, Semantic, Responsive Grid System

Copyright &copy; 2015, [Brendan Doms](http://www.bdoms.com/)  
Licensed under the [MIT license](http://www.opensource.org/licenses/MIT)


## Use

All you have to do is make rows with a parent that has the "grid" class.

After that, just write out the fractions of the container you want and it should just work!
That includes nesting. For example:

```html
<div class="grid">
	<div class="two-thirds">Lots of room!</div>
	<div class="one-third">Less room!</div>
</div>

<div class="grid">
	<div class="two-thirds">
		<div class="grid">
			<div class="one-half">This is nested.</div>
			<div class="one-fourth">1/4</div>
			<div class="one-quarter">Also 1/4</div>
		</div>
	</div>
	<div class="one-third"></div>
</div>
```


## Browser Support

  * IE 8+
  * Chrome/Safari/WebKit 1+
  * Firefox 1.7+
  * Opera 7+


## Why Another Grid?

There are tons of options out there. You're probably using [Bootstrap](http://getbootstrap.com/)
for something right now. But I think that most grids can be improved upon, and here's why.

### My Only Floats Are Root Beer

If you've ever used a grid that relies on floats then you know that something inevitably goes wrong.
You forget to clear (or someone forgot the browser hack to actually make the clear fix work),
or a "last" class is missing and by the time you've tracked it down your coffee has gone cold.
Chilled coffee is great, but coffee that was intended to be hot and is now sitting at room temp?
Nobody wants that.

Sadly, most of the other popular methods also have critical flaws.
My previous go to was inline-blocks, but they suffer from an issue called
[bikeshedding](http://www.w3.org/TR/2011/WD-css3-text-20110412/#white-space-collapsing)
that at this point does not have a single way around it that works 100% of the time.

Since the popular options rely on (inconsistent) hacks to get things right, this is a less than optimal situation.
Of course, there's a new standard in the works trying to fix it all, called
[flexbox](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Flexible_boxes).
It's really nice, and the future is headed that way,
but its not finalized and the browser support is still terrible.

The less talked about option is to use tables, which may sound surprising but it turns out to be
(at least in my opinion) the most elegant solution and in general works back down to IE8 without hacks.
[Table Grid](http://mdo.github.io/table-grid/) is a nice example of this method,
and very close to what I ended up writing myself.

### Don't Speak in Code

Let's assume you're ok with floats or your QA process is perfect at catching visual regressions.
Your grid probably still has cryptic, completely-not-semantic names for its classes.
Do you know what "span-12" means by itself? Is it something 12 spans long? How long is a span?
Or does it span 12 units out of...24? 36? Maybe it's a reference to December and spanning the whole year.
Just looking at the HTML it's impossible to tell.
And I think your code should talk to you clearly.

### Fixing Widths

[YUI Grids](http://yuilibrary.com/yui/docs/cssgrids/) has semantic naming,
but then they go and use fixed widths for everything.
In a responsive world this just seems crazy to me.
I've done it before and it's incredibly hard to manage,
especially if you're working across a large number of break points.
Why not use percents and then set a parent width (or max-width) once?
Think of how much less math you'll be doing when you have to add another break point.
You just need one calculation instead of dozens. And less math means more time to party.

[Justify](http://justifygrid.com/) has an interesting approach to this, but they use fixed width gutters.
I don't have a problem with that inherently, but integrating them into the grid system
means that changing the width of the gutter requires changing everything about the grid.
It also means that a column that says it takes up half the page actually takes up
some bizarre number of pixels equal to half the page minus the gutter.
So I'd rather leave that part up to the individual implementers. You might not need gutters.
Or they might have to be changed all the time, like at that decrepit bowling alley down the street.


## My Solution

It seems like what I'm looking for right now is tables with semantic naming and percentage widths.
So that's what I did.


## Name

It's Greek for "order", "law", or "arrangement", inspired by the associated goddess,
[Eunomia](http://en.wikipedia.org/wiki/Eunomia_%28goddess%29).
