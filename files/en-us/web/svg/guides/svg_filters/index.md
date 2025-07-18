---
title: SVG filters
slug: Web/SVG/Guides/SVG_filters
page-type: guide
sidebar: svgref
---

SVG allows us to use similar tools as the bitmap description language such as the use of shadow, blur effects or even merging the results of different filters. With the filter element `<filter>` it is possible to add these effects and later on attach them to an object.

Filters act like layers. When creating them, try applying and testing the effect step by step.

This element has different attributes that help us create the clipping region. Between the filter tags, we can define the _primitives_ that allow us to implement the desired effect. One of these primitives is the [`<feGaussianBlur>`](/en-US/docs/Web/SVG/Reference/Element/feGaussianBlur). The keyword [`SourceAlpha`](https://drafts.fxtf.org/filter-effects/#attr-valuedef-in-sourcealpha) identifies the input for this primitive, is in this case input `in`. The amount of blur to be applied is done using the `stdDeviation` attribute.

## SVG filter example

```html
<defs>
  <filter id="drop-shadow">
    <feGaussianBlur in="SourceAlpha" stdDeviation="3" />
  </filter>
</defs>

<g id="ghost" filter="url(#drop-shadow)">
  <!--Ghost drawing in here-->
</g>
```

The above example will not produce the desired output. Instead we need to add more filter primitives which will produce the desired rendering. By adding `feoffset` and `result`, the effect layer is defined.

`<result>` attribute is a reference that can be used later. It is quite different to an XML id and only can be referenced within the actual `filter`. **`<feoffset>`** primitive has the blur result from the Gaussian blur. **`<feMerge>`** primitive contains the nodes **`<feMergeNode>`** taking as input the result offsetBlur, this will allow it to appear below the `sourceGraphic`.

## Implementation of more primitives

```html
<defs>
  <filter id="drop-shadow">
    <feGaussianBlur in="SourceAlpha" stdDeviation="3" result="blur" />
    <feoffset in="blur" dx="4" dy="4" result="offsetBlur" />
    <feMerge>
      <feMergeNode in="offsetBlur" />
      <feMergeNode in="SourceGraphic" />
    </feMerge>
  </filter>
</defs>
```
