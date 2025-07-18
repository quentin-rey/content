---
title: CSS module landing page template
slug: MDN/Writing_guidelines/Page_structures/Page_types/CSS_module_landing_page_template
page-type: mdn-writing-guide
sidebar: mdnsidebar
---

> [!NOTE]
> _Remember to remove this note block before publishing._
>
> ---
>
> **Page front matter:**
>
> The front matter at the top of the page is used to define "page metadata".
> The values should be updated appropriately for the particular module.
>
> ```md
> ---
> title: CSS NameOfTheModule
> slug: Web/CSS/CSS_NameOfTheModule
> page-type: css-module
> spec-urls:
>   - url1
>   - url2
> sidebar: cssref
> ---
> ```
>
> - **title**
>   - : The `title` value is displayed at the top of the page.
>     This is the text "CSS" followed by the name of the module.
>     For example, the title for the [grid layout](/en-US/docs/Web/CSS/CSS_grid_layout) module landing page is _CSS grid layout_.
> - **slug**
>   - : The `slug` value is the end of the URL path after `https://developer.mozilla.org/en-US/docs/`.
>     This will be formatted as `Web/CSS/CSS_NameOfTheModule`.
>     For example, the slug for the [grid layout](/en-US/docs/Web/CSS/CSS_grid_layout) module landing page is `Web/CSS/CSS_grid_layout`.
> - **page-type**
>   - : The `page-type` value for CSS module landing pages is always `css-module`.
> - **spec-urls**
>   - : The `spec-urls` value is a URL of the specification. In case there is more than one version of the specification that is relevant, present them in a bulleted list. For example, the value for `spec-urls` key for the [filter effects](/en-US/docs/Web/CSS/CSS_filter_effects) module landing page is:
>
>     ```plain
>     - https://drafts.fxtf.org/filter-effects-2/
>     - https://drafts.fxtf.org/filter-effects-1/
>     ```
>
> - **sidebar**
>   - : This is `cssref` for all CSS guide and reference pages.
>     See [Page structures: Sidebars](/en-US/docs/MDN/Writing_guidelines/Page_structures/Sidebars) for details.
>
> ---
>
> _Remember to remove this note block before publishing._

Begin the content on the page with an introductory paragraph, which names the module and says what it does.
This should ideally be one or two short sentences.

## NameOfTheModule in action

In this section, include an example that helps demonstrate the usefulness or the power of various properties provided by this module.
The purpose of this section is to demonstrate a few use cases and to create interest and curiosity in the mind of the readers learning about this module.

Provide a short description of how readers can interact with the example.
Don't go into a lot of detail to explain the example, and don't include code snippets.

Add a live sample that demonstrates the feature using `\{{EmbedLiveSample}}` (see [Live examples](/en-US/docs/MDN/Writing_guidelines/Page_structures/Live_samples) documentation for more information).

## Reference

Create the relevant subsections to list the related properties, functions, data types, and so on.

### Properties

List of all shorthand and longhand properties provided by the module.

### At-rules

List of CSS at-rules provided by the module. Omit this section if there are no relevant CSS at-rules for this module.

### Functions

List of CSS functions provided by the module. Omit this section if there are no relevant CSS functions for this module.

### Data types

List of CSS data types provided by the module. Omit this section if there are no relevant CSS data types for this module.

### Events

List of API events provided by the module. Omit this section if there are no relevant events for this module.

### Interfaces

List the related API and interfaces provided by the module. Omit this section if there are no relevant API interfaces for this module.

## Guides

- LinkToGuide1
  - : Description of the guide in one or two sentences.
- LinkToGuide2
  - : Description of the guide in one or two sentences.

## Related concepts

List all other properties, data types, or glossary terms that may be relevant or related to this module.

## Specifications

`\{{Specifications}}`

_To use this macro, remove the backticks and backslash in the markdown file._

## See also

Include links to reference pages and guides related to the current module. Check the [See also](/en-US/docs/MDN/Writing_guidelines/Writing_style_guide#see_also_section) section in our _Writing style guide_ for more hints and directions.

- link1
- link2
- external_link (year)
