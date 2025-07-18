---
title: <input type="text">
slug: Web/HTML/Reference/Elements/input/text
page-type: html-attribute-value
browser-compat: html.elements.input.type_text
---

{{HTMLSidebar}}

{{HTMLElement("input")}} elements of type **`text`** create basic single-line text fields.

{{InteractiveExample("HTML Demo: &lt;input type=&quot;text&quot;&gt;", "tabbed-shorter")}}

```html interactive-example
<label for="name">Name (4 to 8 characters):</label>

<input
  type="text"
  id="name"
  name="name"
  required
  minlength="4"
  maxlength="8"
  size="10" />
```

```css interactive-example
label {
  display: block;
  font:
    1rem "Fira Sans",
    sans-serif;
}

input,
label {
  margin: 0.4rem 0;
}
```

## Value

The [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) attribute is a string that contains the current value of the text entered into the text field. You can retrieve this using the {{domxref("HTMLInputElement")}} `value` property in JavaScript.

```js
let theText = myTextInput.value;
```

If no validation constraints are in place for the input (see [Validation](#validation) for more details), the value may be an empty string (`""`).

## Additional attributes

In addition to the [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) and the attributes that operate on all {{HTMLElement("input")}} elements regardless of their type, text inputs support the following attributes.

### `list`

The values of the list attribute is the {{domxref("Element.id", "id")}} of a {{HTMLElement("datalist")}} element located in the same document. The {{HTMLElement("datalist")}} provides a list of predefined values to suggest to the user for this input. Any values in the list that are not compatible with the [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) are not included in the suggested options. The values provided are suggestions, not requirements: users can select from this predefined list or provide a different value.

### `maxlength`

The maximum string length (measured in {{glossary("UTF-16", "UTF-16 code units")}}) that the user can enter into the `text` input. This must be an integer value of 0 or higher. If no `maxlength` is specified, or an invalid value is specified, the `text` input has no maximum length. This value must also be greater than or equal to the value of `minlength`.

The input will fail [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) if the length of the text value of the field is greater than `maxlength` {{glossary("UTF-16", "UTF-16 code units")}} long. Constraint validation is only applied when the value is changed by the user.

### `minlength`

The minimum string length (measured in {{glossary("UTF-16", "UTF-16 code units")}}) that the user can enter into the `text` input. This must be a non-negative integer value smaller than or equal to the value specified by `maxlength`. If no `minlength` is specified, or an invalid value is specified, the `text` input has no minimum length.

The input will fail [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) if the length of the text entered into the field is fewer than `minlength` {{glossary("UTF-16", "UTF-16 code units")}} long. Constraint validation is only applied when the value is changed by the user.

### `pattern`

The `pattern` attribute, when specified, is a regular expression that the input's [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) must match for the value to pass [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation). It must be a valid JavaScript regular expression, as used by the {{jsxref("RegExp")}} type, and as documented in our [guide on regular expressions](/en-US/docs/Web/JavaScript/Guide/Regular_expressions); the `'u'` flag is specified when compiling the regular expression so that the pattern is treated as a sequence of Unicode code points, instead of as {{Glossary("ASCII")}}. No forward slashes should be specified around the pattern text.

If the specified pattern is not specified or is invalid, no regular expression is applied and this attribute is ignored completely.

> [!NOTE]
> Use the [`title`](/en-US/docs/Web/HTML/Reference/Elements/input#title) attribute to specify text that most browsers will display as a tooltip to explain what the requirements are to match the pattern. You should also include other explanatory text nearby.

See [Specifying a pattern](#specifying_a_pattern) for further details and an example.

### `placeholder`

The `placeholder` attribute is a string that provides a brief hint to the user as to what kind of information is expected in the field. It should be a word or short phrase that demonstrates the expected type of data, rather than an explanatory message. The text _must not_ include carriage returns or line feeds.

If the control's content has one directionality ({{Glossary("LTR")}} or {{Glossary("RTL")}}) but needs to present the placeholder in the opposite directionality, you can use Unicode bidirectional algorithm formatting characters to override directionality within the placeholder; see [How to use Unicode controls for bidi text](https://www.w3.org/International/questions/qa-bidi-unicode-controls) for more information.

> [!NOTE]
> Avoid using the `placeholder` attribute if you can. It is not as semantically useful as other ways to explain your form, and can cause unexpected technical issues with your content. See [`<input>` accessibility concerns](/en-US/docs/Web/HTML/Reference/Elements/input#accessibility) for more information.

### `readonly`

A Boolean attribute which, if present, means this field cannot be edited by the user. Its `value` can, however, still be changed by JavaScript code directly setting the {{domxref("HTMLInputElement")}} `value` property.

> [!NOTE]
> Because a read-only field cannot have a value, `required` does not have any effect on inputs with the `readonly` attribute also specified.

### `size`

The `size` attribute is a numeric value indicating how many characters wide the input field should be. The value must be a number greater than zero, and the default value is 20. Since character widths vary, this may or may not be exact and should not be relied upon to be so; the resulting input may be narrower or wider than the specified number of characters, depending on the characters and the font ({{cssxref("font")}} settings in use).

This does _not_ set a limit on how many characters the user can enter into the field. It only specifies approximately how many can be seen at a time. To set an upper limit on the length of the input data, use the [`maxlength`](#maxlength) attribute.

### `spellcheck`

The [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck) global attribute is used to indicate whether to enable spell-checking for an element. It can be used on any editable content, but here we consider specifics related to the use of `spellcheck` on {{HTMLElement("input")}} elements. The permitted values for `spellcheck` are:

- `false`
  - : Disable spell-checking for this element.
- `true`
  - : Enable spell-checking for this element.
- `""` (empty string) or no value
  - : Follow the element's default behavior for spell-checking. This may be based upon a parent's `spellcheck` setting or other factors.

An input field can have spell-checking enabled if it doesn't have the [readonly](#readonly) attribute set and is not disabled.

The value returned by reading `spellcheck` may not reflect the actual state of spell-checking within a control, if the {{Glossary("user agent", "user agent's")}} preferences override the setting.

## Using text inputs

`<input>` elements of type `text` create basic, single-line inputs. You should use them anywhere you want the user to enter a single-line value and there isn't a more specific input type available for collecting that value (for example, if it's a [date](/en-US/docs/Web/HTML/Reference/Elements/input/datetime-local), [URL](/en-US/docs/Web/HTML/Reference/Elements/input/url), [email](/en-US/docs/Web/HTML/Reference/Elements/input/email), or [search term](/en-US/docs/Web/HTML/Reference/Elements/input/search), you've got better options available).

### Basic example

```html
<form>
  <div>
    <label for="uname">Choose a username: </label>
    <input type="text" id="uname" name="name" />
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

This renders like so:

{{EmbedLiveSample("Basic_example", 600, 80)}}

When submitted, the data name/value pair sent to the server will be `name=Chris` (if "Chris" was entered as the input value before submission). You must remember to include [`name`](/en-US/docs/Web/HTML/Reference/Elements/input#name) attribute on the {{HTMLElement("input")}} element, otherwise the text field's value won't be included with the submitted data.

### Setting placeholders

You can provide a useful placeholder inside your text input that can provide a hint as to what to enter by including using the [`placeholder`](/en-US/docs/Web/HTML/Reference/Elements/input#placeholder) attribute. Look at the following example:

```html
<form>
  <div>
    <label for="uname">Choose a username: </label>
    <input
      type="text"
      id="uname"
      name="name"
      placeholder="Lower case, all one word" />
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

You can see how the placeholder is rendered below:

{{EmbedLiveSample("Setting_placeholders", 600, 80)}}

The placeholder is typically rendered in a lighter color than the element's foreground color, and automatically vanishes when the user begins to enter text into the field (or whenever the field has a value set programmatically by setting its `value` attribute).

### Physical input element size

The physical size of the input box can be controlled using the [`size`](/en-US/docs/Web/HTML/Reference/Elements/input#size) attribute. With it, you can specify the number of characters the text input can display at a time. This affects the width of the element, letting you specify the width in terms of characters rather than pixels. In this example, for instance, the input is 30 characters wide:

```html
<form>
  <div>
    <label for="uname">Choose a username: </label>
    <input
      type="text"
      id="uname"
      name="name"
      placeholder="Lower case, all one word"
      size="30" />
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

{{EmbedLiveSample('Physical_input_element_size', 600, 80)}}

## Validation

`<input>` elements of type `text` have no automatic validation applied to them (since a basic text input needs to be capable of accepting any arbitrary string), but there are some client-side validation options available, which we'll discuss below.

> [!NOTE]
> HTML form validation is _not_ a substitute for server-scripts that ensure the entered data is in the proper format. It's far too easy for someone to make adjustments to the HTML that allow them to bypass the validation, or to remove it entirely. It's also possible for someone to bypass your HTML entirely and submit the data directly to your server. If your server-side code fails to validate the data it receives, disaster could strike when improperly-formatted data (or data which is too large, is of the wrong type, and so forth) is entered into your database.

### A note on styling

There are useful pseudo-classes available for styling form elements to help the user see when their values are valid or invalid. These are {{cssxref(":valid")}} and {{cssxref(":invalid")}}. In this section, we'll use the following CSS, which will place a check (tick) mark next to inputs containing valid values, and a cross (X) next to inputs containing invalid values.

```css
div {
  margin-bottom: 10px;
  position: relative;
}

input + span {
  padding-right: 30px;
}

input:invalid + span::after {
  position: absolute;
  content: "✖";
  padding-left: 5px;
}

input:valid + span::after {
  position: absolute;
  content: "✓";
  padding-left: 5px;
}
```

The technique also requires a {{htmlelement("span")}} element to be placed after the form element, which acts as a holder for the icons. This was necessary because some input types on some browsers don't display icons placed directly after them very well.

### Making input required

You can use the [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) attribute as an easy way of making entering a value required before form submission is allowed:

```html
<form>
  <div>
    <label for="uname">Choose a username: </label>
    <input type="text" id="uname" name="name" required />
    <span class="validity"></span>
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

```css hidden
div {
  margin-bottom: 10px;
  position: relative;
}
input + span {
  padding-right: 30px;
}
input:invalid + span::after {
  position: absolute;
  content: "✖";
  padding-left: 5px;
}
input:valid + span::after {
  position: absolute;
  content: "✓";
  padding-left: 5px;
}
```

This renders like so:

{{EmbedLiveSample('Making_input_required', 600, 100)}}

If you try to submit the form with no search term entered into it, the browser will show an error message.

### Input value length

You can specify a minimum length (in characters) for the entered value using the [`minlength`](/en-US/docs/Web/HTML/Reference/Elements/input#minlength) attribute; similarly, use [`maxlength`](/en-US/docs/Web/HTML/Reference/Elements/input#maxlength) to set the maximum length of the entered value, in characters.

The example below requires that the entered value be 4–8 characters in length.

```html
<form>
  <div>
    <label for="uname">Choose a username: </label>
    <input
      type="text"
      id="uname"
      name="name"
      required
      size="10"
      placeholder="Username"
      minlength="4"
      maxlength="8" />
    <span class="validity"></span>
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

```css hidden
div {
  margin-bottom: 10px;
  position: relative;
}
input + span {
  padding-right: 30px;
}
input:invalid + span::after {
  position: absolute;
  content: "✖";
  padding-left: 5px;
}
input:valid + span::after {
  position: absolute;
  content: "✓";
  padding-left: 5px;
}
```

This renders like so:

{{EmbedLiveSample('Input_value_length', 600, 100)}}

If you try to submit the form with less than 4 characters, you'll be given an appropriate error message (which differs between browsers). If you try to enter more than 8 characters, the browser won't let you.

> [!NOTE]
> If you specify a `minlength` but do not specify `required`, the input is considered valid, since the user is not required to specify a value.

### Specifying a pattern

You can use the [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) attribute to specify a regular expression that the inputted value must match in order to be considered valid (see [Validating against a regular expression](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation#validating_against_a_regular_expression) for a crash course on using regular expressions to validate inputs).

The example below restricts the value to 4-8 characters and requires that it contain only lower-case letters.

```html
<form>
  <div>
    <label for="uname">Choose a username: </label>
    <input
      type="text"
      id="uname"
      name="name"
      required
      size="45"
      pattern="[a-z]{4,8}" />
    <span class="validity"></span>
    <p>Usernames must be lowercase and 4-8 characters in length.</p>
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

```css hidden
div {
  margin-bottom: 10px;
  position: relative;
}

p {
  font-size: 80%;
  color: #999;
}

input + span {
  padding-right: 30px;
}

input:invalid + span::after {
  position: absolute;
  content: "✖";
  padding-left: 5px;
}

input:valid + span::after {
  position: absolute;
  content: "✓";
  padding-left: 5px;
}
```

This renders like so:

{{EmbedLiveSample('Specifying_a_pattern', 600, 130)}}

## Examples

You can see good examples of text inputs used in context in our [Your first HTML form](/en-US/docs/Learn_web_development/Extensions/Forms/Your_first_form) and [How to structure an HTML form](/en-US/docs/Learn_web_development/Extensions/Forms/How_to_structure_a_web_form) articles.

## Technical summary

<table class="properties">
  <tbody>
    <tr>
      <td><strong><a href="#value">Value</a></strong></td>
      <td>
        A string representing the text contained in
        the text field.
      </td>
    </tr>
    <tr>
      <td><strong>Events</strong></td>
      <td>
        {{domxref("HTMLElement/change_event", "change")}} and
        {{domxref("Element/input_event", "input")}}
      </td>
    </tr>
    <tr>
      <td><strong>Supported Common Attributes</strong></td>
      <td>
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete"><code>autocomplete</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#list"><code>list</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#maxlength"><code>maxlength</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#minlength"><code>minlength</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#pattern"><code>pattern</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#placeholder"><code>placeholder</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#readonly"><code>readonly</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#required"><code>required</code></a> and
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#size"><code>size</code></a>
      </td>
    </tr>
    <tr>
      <td><strong>IDL attributes</strong></td>
      <td><a href="/en-US/docs/Web/HTML/Reference/Elements/input#list"><code>list</code></a>, <code>value</code></td>
    </tr>
    <tr>
      <td><strong>DOM interface</strong></td>
      <td><p>{{domxref("HTMLInputElement")}}</p></td>
    </tr>
    <tr>
      <td><strong>Methods</strong></td>
      <td>
        {{domxref("HTMLInputElement.select", "select()")}},
        {{domxref("HTMLInputElement.setRangeText", "setRangeText()")}}
        and
        {{domxref("HTMLInputElement.setSelectionRange", "setSelectionRange()")}}.
      </td>
    </tr>
    <tr>
      <td><strong>Implicit ARIA Role</strong></td>
      <td>with no <code>list</code> attribute:
                <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role">textbox</a></code></td>
      <td>with <code>list</code> attribute: <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role">combobox</a></code></td>
    </tr>
  </tbody>
</table>

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [HTML Forms](/en-US/docs/Learn_web_development/Extensions/Forms)
- {{HTMLElement("input")}} and the {{domxref("HTMLInputElement")}} interface it's based upon.
- [`<input type="search">`](/en-US/docs/Web/HTML/Reference/Elements/input/search)
- {{HTMLElement("textarea")}}: Multi-line text input
