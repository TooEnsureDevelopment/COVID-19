# CSS Grids - QuickerUp

1. Download fire-fox.
    - Best dev tools when working with CSS Grid.
        - example: Actually visualizing the grid layout.

2. Go to code-pen.com
    - Ability to write some quick code.
        - example: CSS Grids, which we'll be going over until you feel comfortable.

> Note: Make sure your in For-fox browser. Nor do you need to create a account on code-pen if you don't wont to.

You'll see three windows:

* HTML
* CSS
* JS

Close js window, only because we're not going to be using js.

>IMG

Also we're going to be using a "CSS Preprocessor" called "SASS".

> Long as you know CSS is all that matters, Sass only makes CSS wayyyy easier to write. 


## Getting Started

Ok bet, now lets write some quick HTML.

**HTML**

```ruby
    <div class="container">
        <div class="item item--1"></div>
        <div class="item item--2"></div>
        <div class="item item--3"></div>
        <div class="item item--4"></div>
        <div class="item item--5"></div>
        <div class="item item--6"></div>
    </div>
```

> Also you can type .container>.item.items--$*6 then press tab, same result

Assign a random "Color Name" inside the HTML elements. (assigned numbers optional)

```ruby
    <div class="container">
        <div class="item item--1">1: Red</div>
        <div class="item item--2">2: Orange</div>
        <div class="item item--3">3: Pink</div>
        <div class="item item--4">4: Gray</div>
        <div class="item item--5">5: Brown</div>
        <div class="item item--6">6: Green</div>
    </div>
```

There, lets give it some simple styles.

> You can literally copy and paste this part if you wont.

**SCSS**

```ruby
    .container {
        background-color: #eee;  # Set background color to gray
        width: 1000px;          # 1000px only because, keeping it simple
        margin: 0 auto;         # Centering in viewport (feel free to put 30px rather then 0)

    }
```
We might as well add and style the children elements to.

```ruby

    .container {
    ...         # ... Only representing some other text/code 
        .item {
            border: 1px solid black;
            font-size: 2rem;
            color: white;
            padding: 1rem;

            &--1 {
                background-color: red;
            }
            &--2 {
                background-color: orange;
            }
            &--3 {
                background-color: pink;
            }
            &--4 {
                background-color: grey;
            }
            &--5 {
                background-color: brown;
            }
            &--6 {
                background-color: green;
            }
        }
```

Following SCSS code should look like:

```ruby
    .container {
        background-color: #eee;  
        width: 1000px;         
        margin: 30px auto;

        .item {
            border: 1px solid black;
            font-size: 2rem;
            color: white;
            padding: 1rem;

            &--1 {
                background-color: red;
            }
            &--2 {
                background-color: orange;
            }
            &--3 {
                background-color: pink;
            }
            &--4 {
                background-color: grey;
            }
            &--5 {
                background-color: brown;
            }
            &--6 {
                background-color: green;
            }
        }
    }
```

>IMG_Onlysytle

## The Grid

Ayeeeeeee, so here's how we display a grid.

```ruby
    .container {
        ...             # ... Only representing some other text 

        display: grid;  # Just set display to grid
    }
    ...
```

There, we turned our ```.container``` class to a grid.

Yet there'll not be any changes because we need to define the columns and rows.

Just because, lets say we only want 3 columns.

Here's how we can do that.

```ruby
    .container {
        ...

        display: grid;  # Turning container to grid
        grid-template-columns: 2fr 1fr 1fr; # Defining 3 grid columns

    }
```

>IMG__3colimg

> fr only stands for fractional unit and since two grid cells are set to 1fr they column will be set equal. 2fr will be double 1fr.

Yet what if we wanted 8 or 12 columns, yea that'll a be lots of ```1fr```'s. (lol).

A better way of doing this is by using ```repeat()```

```ruby
    .container {
        ...

        display: grid;  # Turning container to grid
        grid-template-columns: 2fr repeat(2, 1fr); # same as 2fr 1fr 1fr
    }
```

Lets give the grid a gap so we can see a bit better.


In most cases we don't have to worry about ```grid-template-rows``` because there're automatically created as we reach the column limit.

Although I still find myself using them a-lot.

So just for the heck of it, lets define rows and also set each grid cell equal.

```ruby
    .container {
        ...
        display: grid;  # Turning container to grid
        grid-template-columns: repeat(3, 1fr); # same as 1fr 1fr 1fr (3 times)
        grid-template-rows: repeat(2, 150px);     # same as 150px 150px (twice)
        grid-gap: 5rem;       # This grid gap is just to get better visual
    }
```

>IMG__ gridrowcol

You're probably curious. "Well, what if I want to implicitly position a element to a row without filling the column".

## Positioning grid items

So here's when fire-fox comes in handy.

Right click the screen and click inspect the page. (Mines say "inspect Element")

This will bring up fire-fox dev tools.

>IMG-inspctor

Now if you find the container class you'll see a small grid button.


>IMG-findclasstool

Here you'll see small button with text grid.

Click and watch a visual grid outline appear.

>IMG-clickgrid

Ok look closely at the numbering.

Between row 1 and 2 you have a column, and between 2 and 3 you have a column.

Same with column between column 1 and 2 you have a row, and between 2 and 3 you have a row and so on.

Ok, ok, ok. your'll literally done with basic grids once you can position the cells.

Sooooooooooo easy, just define ```grid-row``` or grid-column``` within that element class.

Then tell the grid where you'll like to place that element.

Lets say we want to move the green element where the red element is.
 
Well according to the the visual grid that fire-fox provides us.

We can move the element to ```grid-row: 1/2;```.

```ruby
    .item {
        ...

        &--6 {
            background-color: green;
            grid-row: 1/2;
        }
    }
```

>IMG-green1/2

lol, There, how hard was that.

In fact, if we actually ment to position in the orange element, we get add ```grid-column: 3/4;```

```ruby
    .item {
        ...

        &--6 {
            background-color: green;
            grid-row: 1/2;
            grid-column: 3/4;
        }
    }
```

>IMG-greeen3/4

Lets also move the red item under the green item.

```ruby
    .item {
        &--1 {
            background-color: red;
            grid-row: 2/3;
            grid-column: 3/4;
        }
        ...
    }
```

>img-red2/3

**Spaning**

Ok last but not least.

There's something called a "Implicit" and "Explicit" grid.

* Implicit
    - Is when you define the item row or column.
        - Example: grid-row: 2/3; and/or grid-column: 3/4;

* Explicit
    - Is the unassigned row or column

As you seen in the exercise above, CSS grid agorythem will automatically reposition the "Explicit" item to the last empthy space availible, when we "Implicitly" position a item within its "Explicit" space.

>LOL hope that make a since.

For instance, the "brown" item is currently has a Explicit position. (Unless you got to happy and start *Implicitly* moving items around, lol)

The "gray" item also hasn't been manually positioned.

>IMG

Perhap we want to "Implicitly" position the "brown" item where the "gray" item is located.

> I'll let you figure how to position them

>IMG

Great, what if we *Implicitly* set the "gray" item back to its position.

```ruby
    &--5 {
        background-color: brown;
        grid-column: 1/2;
        grid-row: 2/3;
    }
```

>IMG-brown1/2

I'm pretty sure you guessed it. The item is hidden behind the "brown" item.

Just to prove it we can span the "gray" item accross multiple columns.

```ruby
.item {
    ...
    &--4 {
        background-color: grey;
        grid-column: 1/ span 2;     # This will span two columns
        grid-row: 2/3;
    }
    ...
}
```

>IMG-gray1/2span

Ok, even better there's a few ways we could of achieved this

* ```grid-column: 1/ span 2;```
    - This will span 2 column cells

* ```grid-column: 1/ 3;```
    - This would of been tecnically no difference from above

* ```grid-column: 1/ -1;```
    - Now this tells that cell to span accross the remainder of availiable space.


For instance, if we move the color *red* item to ```grid-row: 4/5;```

We have some availiable space.

>img-AS

By setting the *gray* item to ```grid-column: 1/ -1;```.

It'll span accross the remainder of availiable space

> IMG-red4

> Now see what happins if you move the *red* item back.


Ayyyyyyeeeeee Ok bro, 

thats really all for now, here go a challage so that you get use to the grid structure.


Try and create this layout.



