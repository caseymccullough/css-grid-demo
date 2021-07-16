![](/ga_cog.png)

---

Title: Introduction to CSS Grid<br>
Author: Joe Keohan
Competencies: CSS, Grid<br>
Prerequisites: HTML, CSS basics<br>
Duration: 90 - 120min

---

# CSS GRID

![](https://imgur.com/IqIRrx1.png)

## The Concept Of Grid

Although `CSS Grid` wasn't available until 2017 the concept of `grid` isn't new. [Bootstrap](https://getbootstrap.com/docs/4.1/layout/grid/) was built on  arranging content in rows and columns, essentially creating a grid. 

They use classes such as `.container` to define the parent container and then `.row` and `.col` to define the rows/columns.

<img src="https://i.imgur.com/1T7SgNe.png" />

```html
<div class="container">
	<div class="row">
		<div class="col">Column</div>
		<div class="col">Column</div>
	</div>
	<div class="row">
		<div class="col">Column</div>
		<div class="col">Column</div>
	</div>
</div>
```

Bootstrap is still one of the most widely used front end layout frameworks along with `Foundation, Materialize, Semantic UI` and the list goes on. This article does a good job of discussing the pro's and con's of 11 of them, including the ones just mentioned.

[11 Best CSS Frameworks To Look Forward In 2020](https://www.lambdatest.com/blog/best-css-framework-2020/)

<hr>

### What is CSS Grid?

So far we've been using `Flexbox` to arrange content. It's very powerful and something we will continue to work with even with the introduction of CSS Grid. It is however only `one-dimensional`.

<img src="https://i.imgur.com/5NetjtO.png" width=500/>

CSS Grid Layout is a **two-dimensional layout** system (which means it includes both columns and rows).

<img src="https://i.imgur.com/55JCwW4.png" width=500/>

Both `Flexbox` and `CSS Grid` almost always work together with `CSS Grid` being applied to the overall layout and `Flexbox` to the content.

<img src="https://i.imgur.com/zO6XljL.png" width=500/>

### Can I use Grid?

Yes as CSS Grid is supported on almost all modern browsers.

You can always check out [caniuse.com](http://caniuse.com/) to ensure that you are able to use Grid on a specific browser.

<img src="https://i.imgur.com/j1qTzte.png" />

#### Browser Compatibility

Some browsers do require a specific prefix naming convention in order to apply certain properties so we can use [shouldiprefix](http://shouldiprefix.com/) to determine what those are and implement when and where needed, such as IE.

<img src="https://i.imgur.com/V7eggiG.png">

Below is an example of adding grid for all the browsers that support Grid and for IE compatibility.

```css
.grid-container {
	display: -ms-grid;
	display: grid;
}
```

## Working With CSS Grid

Grid is the most robust layout system in CSS. You utilize Grid by applying CSS rules to both the parent `(Grid Container)` and it's children `(Grid Items)`, much like we did with Flexbox.

During the lecture we will reference [A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/) as our go to guide so let's spend a few minutes taking a look at the docs before moving on.

### Basic Terminology

Here are some of the terms we will need to understand when working with CSS Grid.

- **Grid container** - An element that defines a grid-formatting context for its contents. (Parent)

- **Grid item** - An element that participates in grid layout within a grid-formatting context. (Children)

- **Grid track** - A continuous run between two adjacent grid lines. A grid row or column.

- **Grid cell** - Any space bounded by four grid lines, with no grid lines running through it.

- **Grid area** - Any rectangular area bounded by four grid lines and made up of one or more grid cells.

<img src="https://imgur.com/41BYy6R.png" width=600/>

## Today's Build

For today's build we will focus on building out a simple web site where we will `CSS Grid` to arrange the overall layout and then `Flexbox` for the content, which in this case is only the nav.

The image on the right is being displayed via the `Firebox` DevTools. It provides much better support when working with CSS Grid and adds a Grid overlay to visualize the grid.

<img src="https://i.imgur.com/eB8b93V.png" width=800/>

### Getting Started

#### Starter-Code Directory

- cd into the `starter_code` folder
- open in vscode: `code .`
- Inside there are three files `index.html`, `style-main.css` and `style-grid.css`
- We will be working in `style-grid.css` to apply all CSS Grid settings
- Open `index.html`
- Copy the url and paste into `Firefox`

You should see the following layout.

<!-- <img src="https://i.imgur.com/An2ucka.png" /> -->
<!-- <img src="https://i.imgur.com/6Qjfwts.png" width=500> -->
<!-- <img src="https://i.imgur.com/ru5DqU2.png" width=500> -->

<img src="https://i.imgur.com/AoQEeiB.png" width=500/>

<br>
<br>

Let's take a look at the body of the HTML as well so we can see the overall structure.

```html
<body>
	<div class="container">
		<header>
			<h2>Header</h2>
			<p>This is where the logo and navigation would go.</p>
		</header>
		<main class="main-content">
			<section class="section1">
				<h1>Section #1</h1>
				<p>This is where the main bulk of the document content would go.</p>
			</section>
			<section class="section2">
				<h2>Section #2</h2>
				<p>This element we use to organize more content</p>
			</section>
			<section class="section3">
				<h2>Section #3</h2>
				<p>This element we use to organize more content</p>
			</section>
			<aside class="sidebar sidebar1">
				<h2>Aside #1</h2>
				<p>The place where things of less relevance appears.</p>
			</aside>
			<aside class="sidebar sidebar2">
				<h2>Aside #2</h2>
				<p>The place where things of less relevance appears.</p>
			</aside>
		</main>
		<footer>
			<h2>Footer</h2>
			<p>The place where site nav and other meta info typically appears.</p>
		</footer>
	</div>
</body>
```

The one element that appears to contain all the key elements we will target is `.container` which is the same class name assigned to the element that Bootstrap uses to organize it's content.

For our implementation this element does not need to be called `.container` but it does represent a naming convention used in front end web development.

```html
<div class="container"></div>
```

#### Firefox DevTools

Now open `DevTools` in `Firefox`. It uses the same shortcut keys as Chrome: `cmd + option + i`. 

Once it's open click on the `<div class="container">` element in hte `Inspector`. 

We should see the following:

<img src="https://i.imgur.com/EfMVHEf.png" />

On the right side we can see that it provides specific support for Flexbox and Grid

<img src="https://i.imgur.com/ZkM3b3R.png" width=300/>

Since Grid has yet been applied there is no info to display. 

So let's get our Grid on!

#### Borders...Borders...Borders..

Before we define any additional Grid settings let's turn on borders for all elements so we can clearly see their dimensions.  

Add the following to `style-grid.css`.

```
* {
  border: 1px solid;
}
```

## Creating Our Grid

Let's assign Grid to the `.container`. We must keep in mind only direct children of the parent will be able to work with Grid and that grandchild elements cannot be targeted. It works in a `parent > direct child` relationship which was also true for Flexbox.

**style-grid.css**

```css
.container {
  display: grid;
}
```

Firefox should also automatically update and we will see the following:

<img src="https://i.imgur.com/Oisvv2u.png" width=400/>

Now having worked with Flexbox already we might have assumed that Grid would have kicked in and applied some default settings which would have a direct and immediate visual affect on the child elements. 

Although Grid is now being applied it doesn't have the same effect as Flexbox.

<img src="https://i.imgur.com/9EKQD7D.png" width=500/>



### Viewing Grid


We've only turned on Grid and now it's waiting for us to define set columns and rows to place our content.  Before we do so let's click on `div.container` to see the available Grid settings.

<img src="https://i.imgur.com/MII5ISf.png" width=300/>

We should see the following in the browser. By default Grid creates a single column and assigns all the immediate children to their own row. We can see that this corresponds to `Header` - `Main` - `Footer`.

<!-- <img src="https://i.imgur.com/IPSjD67.png" width=500/> -->

<!-- <img src="https://i.imgur.com/iYB4sYv.png" width=500/> -->

<img src="https://i.imgur.com/wMAI7Gh.png" width=500/>

Those numbers are important and we will use them as a reference later when we assign elements to parts of the grid.

#### Explicit vs Implicit Grids

- An **Explicit Grid** is when we manually define our grid using `grid-template-rows`, `grid-template-columns` and `grid-areas`.
- An **Implicit Grid** is formed when there are more grid items than cells in the grid or when a grid item is placed outside of the explicit grid, the grid container automatically generates grid tracks.

Since we haven't assigned any elements to columns or rows as of yet Grid is working in `Implicit Grid` mode where it is taking on the job of creating new rows for content.

#### Assigning Rows and Columns

We will use the following properties to define our rows and columns:

- `grid-template-columns`
- `grid-template-rows`

They both can be assigned values such as `px`, `%`, `em`, but there is a new value that Grid provides called a `fractional unit`.

Let's test out assigning both `fr` and `%` to see how they might differ.

```
.container {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 25% 50% 25%;
}
```

Since there is only 1 column we won't see any change there but the rows now appear to be affected. Using `%` doesn't take into consideration the actual content and even cuts off part of the last `aside`.

<img src="https://i.imgur.com/I2N2jFI.png" width=500/>

Let's assign the rows `fr` units and see how that affects them.

```
.container {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 1fr 1fr 1fr;
}
```

Ok so thats looks much better.  However Grid is now assigning just a bit more height to both the `Header` and `Footer` than they need.

<img src="https://i.imgur.com/fx9e2b9.png" width=500/>

<!-- <img src="https://i.imgur.com/rjsBEoq.png" width=500/> -->
<!-- <img src="https://i.imgur.com/KtyYOSV.png" width=500/> -->

<!-- <img src="https://i.imgur.com/tE0JCbC.png" width=500/> -->

#### Using `auto`

Grid has another way to guarantee that the `Header` and `Footer` are assigned only the height needed based on their content. We can assign those rows a value of `auto`.

```
.container {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: auto 1fr auto;
}
```

### Nested Grids

Assigning Grid to the container and defining the `rows/columns` really is enough to meet the first phase of the design. The main section will however require a bit more finesse in arranging the elements. 

Since Grid only has an effect on immediate children we need to add grid to the `.main-content` element as well so that we can apply Grid there as well.

```
.main-content {
  display: grid;
}
```

We should see that the elements expanded just a bit to take up the remaining space.

In DevTools we can also see that we can overlay Grid on the main element as well.

<img src="https://i.imgur.com/zK1Lgwm.png" />

Here is the Grid.

<img src="https://i.imgur.com/TsUreuY.png" width=500/>

#### Defining Rows/Columns

Based on the design it looks like there will be 3 columns and 3 rows. So let's add the css to create that layout.

```
.main-content {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
}
```

<img src="https://i.imgur.com/CmDE9Po.png" width=500/>

SInce all of the rows are the same `fr` we can shorten that syntax using the `repeat` keyword.  `repeat` takes in 2 values

- `first:` how many rows or columns
- `second:` the size for each of them

```
.main-content {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  grid-template-rows: repeat(3, 1fr);
}
```

#### Assigning the Elements to Rows/Columns

Just like flexbox, child elements of a Flexbox container are provided additional properties that affect the child directly. This is also the same for Grid which uses the following three ways to place the elements.

**Columns**

- grid-column-start / grid-column-end
- grid-column: 1 / 3 or 1 / span 2
- grid-area: main or footer

**Rows**

- grid-row-start / grid-row-end
- grid-row: 1 / 3 or 1 / span 2
- grid-area: main or footer

For this lecture we will only focus on `grid-row` and `grid-column`.

#### Section #1

Let's target the first section and place it into position. This is where those line numbers come into play. It seems the element should span 1 column and 3 rows.

Let's see what that translates into using `grid-column` and `grid-row` where we target the line numbers.

```css
.main-content .section1 {
	grid-column: 1 / 2;
	grid-row: 1 / 4;
}
```

<img src="https://i.imgur.com/eNGNjZu.png" width=500/>

Since the element is essentially spanning 3 rows we can also write it using the `span` keyword.

```css
.main-content .section1 {
	grid-column: 1 / 2;
	grid-row: 1 / span 3;
}
```

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - 5min

- Take a moment to examine the final layout design
- Try and target the following elements in CSS and add the grid-column and grid-row values to move them into place:

  - .section2
  - .section3
  - .sidebar1
  - .sidebar2


<hr>

#### Remaining Elements

Now that you had a chance to work through it on your own let's use the following to assign the remaining elements to columns and rows.

<details>
<summary>Solution</summary>

```css
.main-content .section2 {
	grid-column: 2 / 4;
	grid-row: 1 / 2;
}

.main-content .section3 {
	grid-column: 2 / 4;
	grid-row: 2 / 3;
}

.main-content .sidebar1 {
	grid-column: 3 / 4;
	grid-row: 3 / 4;
}

.main-content .sidebar2 {
	grid-column: 2 / 3;
	grid-row: 3 / 4;
}
```

</details>
<br>

Here is what it should look like now.

<img src="https://i.imgur.com/f7zhOHu.png"  width=500/>

#### Grid-Gap

So far so good. If we take a look at the final design we still need to create space between the elements in `.main-content`.

<img src="https://i.imgur.com/ejhRZe1.png" width=500/>

<hr>

Well Grid makes it even easier to create that space. It provides the following properties to do this.

- `grid-column-gap`
- `grid-row-gap`
- `grid-gap` - wraps up both into one property

Let's assign `grid-gap`.

```css
.main-content {
	display: grid;
	grid-template-columns: 2fr 1fr 1fr;
	grid-template-rows: repeat(3, 1fr);
	grid-gap: 10px;
}
```

Since that worked so well let's also apply grid-gap to `.container`

```css
.container {
	display: grid;
	grid-template-columns: 1fr;
	grid-template-rows: auto 1fr auto;
	grid-gap: 10px;
}
```

<img src="https://i.imgur.com/51hdOvc.png" width=500/>

### Flexbox and CSS Grid - Together

Both Flexbox and CSS Grid are almost always used in tandem. As has already been mentioned Grid is use for the overall layout and Flexbox for content. 

So let's add some content that you are familiar with such as a nav.

Let's edit the Header element to comment out the existing code.

```html
<header>
	<!-- <h2>Header</h2>
  <p>This is where the logo and navigation would go.</p> -->
</header>
```

And now add the following navigation elements.

```html
<header>
	<!-- <h2>Header</h2>
  <p>This is where the logo and navigation would go.</p> -->
	<nav>
		<img
			src="https://cdn4.iconfinder.com/data/icons/social-media-logos-6/512/121-css3-512.png"
		/>
		<ul>
			<li>Item 1</li>
			<li>Item 2</li>
			<li>Item 3</li>
			<li>Item 4</li>
		</ul>
	</nav>
</header>
```

The Header should now look like this.

<img src="https://i.imgur.com/B9bVjIT.png" width=400/>

Now let's add some Flexbox. First we will target the `nav` and turn on flexbox.

```css
nav {
	display: flex;
}
```

<img src="https://i.imgur.com/4hBigZU.png" width=100 />

That doesn't look very appealing. Let's move the ul to the right using `justify-content` and center the content using `align-items` which should also fix the image.

```css
nav {
	display: flex;
	justify-content: space-between;
	align-items: center;
}
```

That looks better. Now let's target the ul.

```css
nav ul {
	display: flex;
}
```

<img src="https://i.imgur.com/6y4l0VI.png" />

### Final Edits

Our last edit to css will be remove the borders around all the elements.

```css
* {
	/* border: 1px solid; */
}
```

And turn off the Grid overlay in Firefox.

<img src="https://i.imgur.com/RjGePIe.png" width=400/>

And our final design should look like this.

<img src="https://i.imgur.com/UihbVxH.png" width=500/>

### Resources

- [11 Best CSS Frameworks To Look Forward In 2020](https://www.lambdatest.com/blog/best-css-framework-2020/)
- [supporting-css-grid-in-internet-explorer](https://medium.com/@elad/supporting-css-grid-in-internet-explorer-b38669e75d66)
- [Complete-guide-grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [ss-grid-understanding-grid-gap-and-fr-vs-auto-unit](https://www.rawkblog.com/2018/03/css-grid-understanding-grid-gap-and-fr-vs-auto-units/)
