# enno

A simple, powerful, class-based grid system.


### Installation

Just add `enno.scss` or `enno.styl` to your project and `@import` it.


### Philosophy

Enno is similar in markup to Bootstrap or Foundation: `container > row > columns`

The difference is Enno uses `calc()` so you can have fixed gutters. There are also a few helpful classes that allow you to give a row a background as well as set a row to only contain equally sized columns (like `flex: auto` without flexbox).

It removes the `.columns` class that Foundation has, and removes the `.col-` prefix Bootstrap has while still being readable.

Enno is a `display: inline-block` grid system so you can horizontally, vertically, left, right, top, bottom, or simply dead center elements within a wrapper. Simply apply `text-align: foo` to your row and/or `vertical-align: foo` to your columns (I'll add helper classes for this sometime). It handles the whitespace issue by resetting `font-size: 0` for the row, and then setting `font-size: 1rem` for columns within that row.


### Usage

- `.container` simply applies `max-width: $max-width` (a var you can set) and `margin: auto` to horizontally center your content to the viewport.
- `.row` applies a negative `margin-left` the size of the `$gutter` you've specified. By doing this, we can plop columns into that row all willy nilly and they'll drop to the next line as expected. Read more on [CSSWizardry](http://csswizardry.com/2011/08/building-better-grid-systems/). The downside is these elements can't have a background without it hanging over to the left. Enno has `.bg-` classes you can define to fix this. More on that later.
- `.small-12`, `.medium-12`, `.large-12` are Enno's column classes. The number can be 1-12 by default. You can tweak Enno's `$columns` setting to generate 24 column grids (or whatever you want). Enno is a mobile-first grid system, so start by applying a `.small-12` class for `width: 100%` elements. Add on `.medium-6` to have your columns go from `width: 100%` to half with a gutter. Add on `.large-4` to display 3 columns. Breakpoints can be customized in your `enno.*` file. Try not to add classes where you don't need them. For instance, if you know you want an element to span `width: 100%` at any breakpoint, then just set `.small-12` and no other column classes. By default you have 3 different sizes to work with. You can tweak your `enno.*` file to have more breakpoints by simply duplicating some code and swapping out some names.
- `.gutless` removes gutters from all columns within a row. Apply to a `.row`.
- `.bg-foo` allows you to specify background colors for a row. Apply to a `.row` and customize its style as a `:before` selector like so: `.bg-foo:before { background: tomato; }`. A little verbose, but not used very much and solves a problem with the negative margin grid.
- `.equal` displays children elements as equal widths of each other. As you add items, they will take up an equal width of the container. You don't need the `.row` class for this.


### Examples

```html
<div class="row bg-yellow">
  <div class="small-12 medium-6 large-4">1</div>
  <div class="small-12 medium-6 large-4">2</div>
  <div class="small-12 medium-6 large-4">3</div>
  <div class="small-12 medium-6 large-4">
    <div class="row">
      <div class="small-12 medium-6 large-6">1</div>
      <div class="small-12 medium-6 large-6">2</div>
    </div>
  </div>
</div>
```

```css
.bg-yellow:before {
	background: yellow;
}
```

```html
<div class="equal">
	<div>1</div>
	<div>2</div>
	<div>3</div>
</div>
```
