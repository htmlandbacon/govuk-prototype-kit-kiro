# Layouts and Pages

## Overview

The GOVUK Prototype Kit uses a layout system where pages extend a main layout file. This ensures consistent headers, footers, and navigation across all pages.

## Main Layout

The default layout is `app/views/layouts/main.html`. All pages should extend this layout.

**Basic page structure**:
```nunjucks
{% extends "layouts/main.html" %}

{% block content %}
  <h1 class="govuk-heading-xl">Page title</h1>
  
  <p class="govuk-body">Page content goes here.</p>
{% endblock %}
```

## Content Blocks

The main layout provides these blocks:

- **`content`** - Main page content
- **`head`** - Additional head content
- **`footer`** - Custom footer content
- **`bodyEnd`** - Content at the end of the body

**Example with multiple blocks**:
```nunjucks
{% extends "layouts/main.html" %}

{% block head %}
  <link rel="stylesheet" href="/public/styles/custom.css">
{% endblock %}

{% block content %}
  <h1>Page title</h1>
  {{ govukButton({ text: "Continue" }) }}
{% endblock %}
```

## Custom Layouts

You can create custom layouts for specific sections of your service.

**Example - Service-specific layout**:
```nunjucks
{# app/views/layouts/service.html #}
{% extends "layouts/main.html" %}

{% block content %}
  <div class="govuk-grid-row">
    <div class="govuk-grid-column-two-thirds">
      {% block serviceContent %}
      {% endblock %}
    </div>
  </div>
{% endblock %}
```

**Using custom layout**:
```nunjucks
{% extends "layouts/service.html" %}

{% block serviceContent %}
  <h1>Service page</h1>
{% endblock %}
```

## Page Templates

The kit includes built-in page templates accessible via the "Templates" section in the prototype manager:

- Start page
- Question page
- Check your answers
- Confirmation page

## File Locations

```
app/
├── views/
│   ├── layouts/
│   │   ├── main.html          # Main layout
│   │   └── service.html       # Custom layout (optional)
│   ├── index.html             # Home page
│   ├── start.html             # Start page
│   └── page-name.html         # Other pages
```

## Best Practices

1. **Always extend main.html** - Don't create full HTML documents from scratch
2. **Use content block** - Put all page content in the `content` block
3. **Keep layouts DRY** - Use custom layouts for repeated patterns
4. **Test responsive** - Verify layouts work on mobile devices
