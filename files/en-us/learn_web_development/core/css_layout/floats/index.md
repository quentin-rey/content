---
title: Floats
slug: Learn_web_development/Core/CSS_layout/Floats
page-type: learn-module-chapter
sidebar: learnsidebar
---

{{PreviousMenuNext("Learn_web_development/Core/CSS_layout/Introduction", "Learn_web_development/Core/CSS_layout/Positioning", "Learn_web_development/Core/CSS_layout")}}

Originally for floating images inside blocks of text, the {{cssxref("float")}} property became one of the most commonly used tools for creating multiple column layouts on webpages. With the advent of flexbox and grid it's now returned to its original purpose, as this article explains.

<table>
  <tbody>
    <tr>
      <th scope="row">Prerequisites:</th>
      <td>
        <a href="/en-US/docs/Learn_web_development/Core/Structuring_content"
          >Structuring content with HTML</a
        >,
        <a href="/en-US/docs/Learn_web_development/Core/Styling_basics">CSS Styling basics</a>,
        <a href="/en-US/docs/Learn_web_development/Core/Text_styling/Fundamentals">Fundamental text and font styling</a>,
        familiarity with <a href="/en-US/docs/Learn_web_development/Core/CSS_layout/Introduction">CSS layout fundamental concepts</a>.
      </td>
    </tr>
    </tr>
    <tr>
      <th scope="row">Learning outcomes:</th>
      <td>
        <ul>
          <li>Understand the purpose of floats — for floating images inside columns of text, and other techniques like drop caps and floating inset information boxes.</li>
          <li>Understand that floats used to be used for multiple-column layouts, but this is no longer the case now better tools are available.</li>
          <li>Using the <code>float</code> property to create floats.</li>
          <li>Clearing floats using <code>clear</code>, and the <code>display: flow-root</code> value.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## The background of floats

The {{cssxref("float")}} property was introduced to allow web developers to implement layouts involving an image floating inside a column of text, with the text wrapping around the left or right of it. The kind of thing you might get in a newspaper layout.

But web developers quickly realized that you can float anything, not just images, so the use of float broadened, for example, to fun layout effects such as [drop-caps](https://css-tricks.com/snippets/css/drop-caps/).

Floats have commonly been used to create entire website layouts featuring multiple columns of information floated so they sit alongside one another (the default behavior would be for the columns to sit below one another in the same order as they appear in the source). There are newer, better layout techniques available. Using floats in this way should be regarded as a legacy technique.

In this article we'll just concentrate on the proper uses of floats.

## A float example

Let's explore the use of floats. We'll start with an example involving floating a block of text around an element. You can follow along by creating a new `index.html` file on your computer, filling it with an [HTML template](https://github.com/mdn/learning-area/blob/main/html/introduction-to-html/getting-started/index.html), and inserting the below code into it at the appropriate places. At the bottom of the section, you can see a live example of what the final code should look like.

First, we'll start off with some HTML. Add the following to your HTML body, removing anything that was inside there before:

```html
<h1>Float example</h1>

<div class="box">Float</div>

<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam
  dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus
  ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus
  laoreet sit amet.
</p>

<p>
  Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet
  orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare
  ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse
  ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis
  ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et
  a urna. Ut id ornare felis, eget fermentum sapien.
</p>

<p>
  Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada
  ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed
  est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus
  tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies lectus
  sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis
  vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque
  penatibus et magnis dis parturient montes, nascetur ridiculus mus.
</p>
```

Now apply the following CSS to your HTML (using a {{htmlelement("style")}} element or a {{htmlelement("link")}} to a separate `.css` file — your choice):

```css
body {
  width: 90%;
  max-width: 900px;
  margin: 0 auto;
  font:
    0.9em/1.2 Arial,
    Helvetica,
    sans-serif;
}

.box {
  width: 150px;
  height: 100px;
  border-radius: 5px;
  background-color: rgb(207 232 220);
  padding: 1em;
}
```

If you save and refresh, you'll see something much like what you'd expect: the box is sitting above the text, in normal flow.

### Floating the box

To float the box, add the {{cssxref("float")}} and {{cssxref("margin-right")}} properties to the `.box` rule:

```html hidden
<h1>Float example</h1>

<div class="box">Float</div>

<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam
  dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus
  ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus
  laoreet sit amet.
</p>

<p>
  Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet
  orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare
  ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse
  ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis
  ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et
  a urna. Ut id ornare felis, eget fermentum sapien.
</p>

<p>
  Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada
  ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed
  est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus
  tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies lectus
  sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis
  vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque
  penatibus et magnis dis parturient montes, nascetur ridiculus mus.
</p>
```

```css
.box {
  float: left;
  margin-right: 15px;
  width: 150px;
  height: 100px;
  border-radius: 5px;
  background-color: rgb(207 232 220);
  padding: 1em;
}
```

Now if you save and refresh you'll see something like the following:

{{EmbedLiveSample('Floating_the_box', '100%', 500)}}

Let's think about how the float works. The element with the float set on it (the {{htmlelement("div")}} element in this case) is taken out of the normal layout flow of the document and stuck to the left-hand side of its parent container ({{htmlelement("body")}}, in this case). Any content that would come below the floated element in the normal layout flow will now wrap around it instead, filling up the space to the right-hand side of it as far up as the top of the floated element. There, it will stop.

Floating the content to the right has exactly the same effect, but in reverse: the floated element will stick to the right, and the content will wrap around it to the left. Try changing the float value to `right` and replace {{cssxref("margin-right")}} with {{cssxref("margin-left")}} in the last ruleset to see what the result is.

### Visualizing the float

While we can add a margin to the float to push the text away, we can't add a margin to the text to move it away from the float. This is because a floated element is taken out of normal flow and the boxes of the following items actually run behind the float. You can see this by making some changes to your example.

Add a class of `special` to the first paragraph of text, the one immediately following the floated box, then in your CSS add the following rules. These will give our following paragraph a background color.

```css
.special {
  background-color: rgb(148 255 172);
  padding: 10px;
  color: purple;
}
```

To make the effect easier to see, change the `margin-right` on your float to `margin` so you get space all around the float. You'll be able to see the background on the paragraph running right underneath the floated box, as in the example below.

```html hidden
<h1>Float example</h1>

<div class="box">Float</div>

<p class="special">
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam
  dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus
  ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus
  laoreet sit amet.
</p>

<p>
  Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet
  orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare
  ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse
  ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis
  ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et
  a urna. Ut id ornare felis, eget fermentum sapien.
</p>

<p>
  Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada
  ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed
  est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus
  tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies lectus
  sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis
  vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque
  penatibus et magnis dis parturient montes, nascetur ridiculus mus.
</p>
```

```css hidden
body {
  width: 90%;
  max-width: 900px;
  margin: 0 auto;
  font:
    0.9em/1.2 Arial,
    Helvetica,
    sans-serif;
}

.box {
  float: left;
  margin: 15px;
  width: 150px;
  height: 150px;
  border-radius: 5px;
  background-color: rgb(207 232 220);
  padding: 1em;
}
```

{{EmbedLiveSample('Visualizing_the_float', '100%', 500)}}

The [line boxes](/en-US/docs/Web/CSS/CSS_display/Visual_formatting_model#line_boxes) of our following element have been shortened so the text runs around the float, but due to the float being removed from normal flow the box around the paragraph still remains full width.

## Clearing floats

We've seen that a float is removed from normal flow and that other elements will display beside it. If we want to stop the following element from moving up, we need to _clear_ it; this is achieved with the {{cssxref("clear")}} property.

In your HTML from the previous example, add a class of `cleared` to the second paragraph below the floated item. Then add the following to your CSS:

```css
.cleared {
  clear: left;
}
```

```html hidden
<h1>Float example</h1>

<div class="box">Float</div>

<p class="special">
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam
  dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus
  ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus
  laoreet sit amet.
</p>

<p class="cleared">
  Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet
  orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare
  ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse
  ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis
  ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et
  a urna. Ut id ornare felis, eget fermentum sapien.
</p>

<p>
  Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada
  ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed
  est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus
  tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies lectus
  sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis
  vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque
  penatibus et magnis dis parturient montes, nascetur ridiculus mus.
</p>
```

```css hidden
body {
  width: 90%;
  max-width: 900px;
  margin: 0 auto;
  font:
    0.9em/1.2 Arial,
    Helvetica,
    sans-serif;
}

.box {
  float: left;
  margin: 15px;
  width: 150px;
  height: 150px;
  border-radius: 5px;
  background-color: rgb(207 232 220);
  padding: 1em;
}

.special {
  background-color: rgb(148 255 172);
  padding: 10px;
  color: purple;
}

.cleared {
  clear: left;
}
```

{{EmbedLiveSample('Clearing_floats', '100%', 600)}}

You should see that the second paragraph now clears the floated element and no longer comes up alongside it. The `clear` property accepts the following values:

- `left`: Clear items floated to the left.
- `right`: Clear items floated to the right.
- `both`: Clear any floated items, left or right.

## Clearing boxes wrapped around a float

You now know how to clear something following a floated element, but let's see what happens if you have a tall float and a short paragraph, with a box containing _both_ elements.

### The problem

Change your document so that the first paragraph and the floated box are jointly wrapped with a {{htmlelement("div")}}, which has a class of `wrapper`.

```html live-sample___the_problem
<div class="wrapper">
  <div class="box">Float1</div>

  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus
    aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci,
    pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at
    ultricies tellus laoreet sit amet.
  </p>
</div>
```

In your CSS, add the following rule for the `.wrapper` class and then reload the page:

```css live-sample___the_problem
.wrapper {
  background-color: rgb(148 255 172);
  padding: 10px;
  color: purple;
}
```

In addition, remove the original `.cleared` class:

```css
.cleared {
  clear: left;
}
```

You'll see that, just like in the example where we put a background color on the paragraph, the background color runs behind the float.

```html hidden live-sample___the_problem
<p>
  Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet
  orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare
  ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse
  ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis
  ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et
  a urna. Ut id ornare felis, eget fermentum sapien.
</p>

<p>
  Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada
  ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed
  est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus
  tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies lectus
  sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis
  vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque
  penatibus et magnis dis parturient montes, nascetur ridiculus mus.
</p>
```

```css hidden live-sample___the_problem
body {
  width: 90%;
  max-width: 900px;
  margin: 0 auto;
  font:
    0.9em/1.2 Arial,
    Helvetica,
    sans-serif;
}

.box {
  float: left;
  margin: 15px;
  width: 150px;
  height: 150px;
  border-radius: 5px;
  background-color: rgb(207 232 220);
  padding: 1em;
  color: black;
}
```

{{EmbedLiveSample('the_problem', '100%', 600)}}

Once again, this is because the float has been taken out of normal flow. You might expect that by wrapping the floated box and the text of first paragraph that wraps around the float together, the subsequent content will be cleared of the box. But this is not the case.

### display: flow-root

To solve this problem is to use the value `flow-root` of the `display` property. This exists only to solve this particular problem without using hacks — there will be no unintended consequences when you use it.

```css
.wrapper {
  background-color: rgb(148 255 172);
  padding: 10px;
  color: purple;
  display: flow-root;
}
```

```html hidden
<h1>Float example</h1>
<div class="wrapper">
  <div class="box">Float</div>

  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus
    aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci,
    pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at
    ultricies tellus laoreet sit amet.
  </p>
</div>
<p class="cleared">
  Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet
  orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare
  ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse
  ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis
  ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et
  a urna. Ut id ornare felis, eget fermentum sapien.
</p>

<p>
  Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada
  ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed
  est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus
  tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies lectus
  sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis
  vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque
  penatibus et magnis dis parturient montes, nascetur ridiculus mus.
</p>
```

```css hidden
body {
  width: 90%;
  max-width: 900px;
  margin: 0 auto;
  font:
    0.9em/1.2 Arial,
    Helvetica,
    sans-serif;
}

.box {
  float: left;
  margin: 15px;
  width: 150px;
  height: 150px;
  border-radius: 5px;
  background-color: rgb(207 232 220);
  padding: 1em;
  color: black;
}
```

{{EmbedLiveSample('display_flow-root', '100%', 600)}}

## Test your skills!

You've reached the end of this article, but can you remember the most important information? You can find some further tests to verify that you've retained this information before you move on — see [Test your skills: Floats](/en-US/docs/Learn_web_development/Core/CSS_layout/Test_your_skills/Floats).

## Summary

That's all you need to know about floats. Next up, we'll explore positioning in detail.

{{PreviousMenuNext("Learn_web_development/Core/CSS_layout/Introduction", "Learn_web_development/Core/CSS_layout/Positioning", "Learn_web_development/Core/CSS_layout")}}
