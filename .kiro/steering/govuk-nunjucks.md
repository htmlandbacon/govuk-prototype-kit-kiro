# Nunjucks with GOVUK Design System

## Overview

Nunjucks is the templating engine used by the GOVUK Prototype Kit. It allows you to create reusable templates, components, and layouts.

## GOVUK Design System Components

The kit provides access to GOVUK Design System components through Nunjucks macros.

**Basic component usage**:
```nunjucks
{{ govukInput({
  label: {
    text: "First name"
  },
  id: "first-name",
  name: "first-name"
}) }}
```

**Common components**:
```nunjucks
{{ govukButton({
  text: "Continue"
}) }}

{{ govukCheckboxes({
  name: "countries",
  fieldset: {
    legend: {
      text: "Which countries have you visited?",
      isPageHeading: true
    }
  },
  items: [
    {
      value: "france",
      text: "France"
    },
    {
      value: "spain",
      text: "Spain"
    }
  ]
}) }}

{{ govukSummaryList({
  rows: [
    {
      key: {
        text: "First name"
      },
      value: {
        text: data['first-name']
      }
    }
  ]
}) }}
```

## Data in Templates

Access form data using the `data` object:

```nunjucks
<!-- Display data -->
<p>{{ data['first-name'] }}</p>

<!-- With fallback -->
<p>{{ data['first-name'] or "Not given" }}</p>

<!-- In input value -->
{{ govukInput({
  value: data['first-name']
}) }}
```

## Nested Data

For complex data structures:

```nunjucks
<!-- Access nested data -->
{{ data['claimant']['first-name'] }}

<!-- In component -->
{{ govukInput({
  name: 'claimant[first-name]',
  value: data['claimant']['first-name']
}) }}
```

## Looping

```nunjucks
<!-- Checkbox array as list -->
<ul>
{% for country in data['countries'] %}
  <li>{{ country }}</li>
{% endfor %}
</ul>
```

## Ignoring Inputs

Prefix input names with underscore to prevent storage:

```nunjucks
{{ govukInput({
  name: '_secret'
}) }}
```

## Best Practices

1. **Always use `data` for form values** - This preserves user input on page reloads
2. **Use GOVUK components** - They're tested for accessibility
3. **Keep components simple** - Don't overcomplicate component parameters
4. **Test with real data** - Verify data persistence works correctly
