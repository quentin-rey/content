---
title: top
slug: Web/CSS/top
page-type: css-property
browser-compat: css.properties.top
---

{{CSSRef}}

The **`top`** [CSS](/en-US/docs/Web/CSS) property sets the vertical position of a [positioned element](/en-US/docs/Web/CSS/position). This {{glossary("inset properties", "inset property")}} has no effect on non-positioned elements.

{{InteractiveExample("CSS Demo: top")}}

```css interactive-example-choice
top: 0;
```

```css interactive-example-choice
top: 4em;
```

```css interactive-example-choice
top: 10%;
```

```css interactive-example-choice
top: 20px;
```

```html interactive-example
<section id="default-example">
  <div class="example-container">
    <div id="example-element">I am absolutely positioned.</div>
    <p>
      As much mud in the streets as if the waters had but newly retired from the
      face of the earth, and it would not be wonderful to meet a Megalosaurus,
      forty feet long or so, waddling like an elephantine lizard up Holborn
      Hill.
    </p>
  </div>
</section>
```

```css interactive-example
.example-container {
  border: 0.75em solid;
  padding: 0.75em;
  text-align: left;
  position: relative;
  width: 100%;
  min-height: 200px;
}

#example-element {
  background-color: #264653;
  border: 4px solid #ffb500;
  color: white;
  position: absolute;
  width: 140px;
  height: 60px;
}
```

The effect of `top` depends on how the element is positioned (i.e., the value of the {{cssxref("position")}} property):

- When `position` is set to `absolute` or `fixed`, the `top` property specifies the distance between the element's outer margin of the top edge and the inner border of the top edge of its containing block, or, in the case of [anchor positioned elements](/en-US/docs/Web/CSS/CSS_anchor_positioning/Using) when the {{cssxref("anchor()")}} function is used within the value, relative to the specified [`<anchor-side>`](/en-US/docs/Web/CSS/anchor#anchor-side) edge. The `top` property is [compatible](/en-US/docs/Web/CSS/anchor#compatibility_of_inset_properties_and_anchor-side_values) with the `top`, `bottom`, `start`, `end`, `self-start`, `self-end`, `center`, and `<percentage>` values.
- When `position` is set to `relative`, the `top` property specifies the distance the element's top edge is moved below its normal position.
- When `position` is set to `sticky`, the `top` property is used to compute the sticky-constraint rectangle.
- When `position` is set to `static`, the `top` property has _no effect_.

When both `top` and {{cssxref("bottom")}} values are specified, there are three different cases:

- If `position` is set to `absolute` or `fixed` and {{cssxref("height")}} is unspecified (either `auto` or `100%`), both the `top` and `bottom` values are respected.
- If `position` is set to `relative` or `height` is constrained, the `top` property takes precedence and the `bottom` property is ignored.
- If `position` is set to `sticky`, both `top` and `bottom` values are considered. This means that a sticky element can potentially move up and down within its containing block based on the values of these two properties as long as the element's position box remains contained within its containing block.

## Syntax

```css
/* <length> values */
top: 3px;
top: 2.4em;
top: anchor(bottom);
top: anchor-size(--myAnchor self-block, 10%);

/* <percentage>s of the height of the containing block */
top: 10%;

/* Keyword value */
top: auto;

/* Global values */
top: inherit;
top: initial;
top: revert;
top: revert-layer;
top: unset;
```

### Values

- {{cssxref("&lt;length&gt;")}}
  - : A negative, null, or positive {{cssxref("&lt;length&gt;")}}:
    - for _absolutely positioned elements_, it represents the distance to the top edge of the containing block.
    - for _anchor-positioned elements_, the {{cssxref("anchor()")}} function resolves to a {{cssxref("&lt;length&gt;")}} value relative to the position of the associated _anchor element_'s top or bottom edge (see [Using inset properties with `anchor()` function values](/en-US/docs/Web/CSS/CSS_anchor_positioning/Using#using_inset_properties_with_anchor_function_values)), and the {{cssxref("anchor-size()")}} function resolves to a {{cssxref("&lt;length&gt;")}} value relative to the associated anchor element's width or height (see [Setting element position based on anchor size](/en-US/docs/Web/CSS/CSS_anchor_positioning/Using#setting_element_position_based_on_anchor_size)).
    - for _relatively positioned elements_, it represents the distance that the element is moved below its normal position.

- {{cssxref("&lt;percentage&gt;")}}
  - : A {{cssxref("&lt;percentage&gt;")}} of the containing block's height.
- `auto`
  - : Specifies that:
    - for _absolutely positioned elements_, the position of the element is based on the {{Cssxref("bottom")}} property, while `height: auto` is treated as a height based on the content; or if `bottom` is also `auto`, the element is positioned where it should vertically be positioned if it were a static element.
    - for _relatively positioned elements_, the distance of the element from its normal position is based on the {{Cssxref("bottom")}} property; or if `bottom` is also `auto`, the element is not moved vertically at all.

## Formal definition

{{CSSInfo}}

## Formal syntax

{{csssyntax}}

## Examples

### A positioned element set 10% from the top

```css
body {
  background: beige;
}

div {
  position: absolute;
  top: 10%;
  right: 40%;
  bottom: 20%;
  left: 15%;
  background: gold;
  border: 1px solid blue;
}
```

```html
<div>The size of this content is determined by the position of its edges.</div>
```

{{EmbedLiveSample('Examples','100%','200')}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{cssxref("bottom")}}, {{cssxref("left")}}, and {{cssxref("right")}}
- {{cssxref("inset")}} shorthand
- {{cssxref("inset-block-start")}}, {{cssxref("inset-block-end")}}, {{cssxref("inset-inline-start")}}, and {{cssxref("inset-inline-end")}}
- {{cssxref("inset-block")}} and {{cssxref("inset-inline")}} shorthands
- {{cssxref("position")}}
- [CSS positioned layout](/en-US/docs/Web/CSS/CSS_positioned_layout) module
