# Assets (Sass, JavaScript, CSS)

## Project Structure

### Styles (Sass)

GOVUK Prototype Kit uses Sass (SCSS syntax) for styling. The kit imports a main Sass file that should import all other styles.

**Location**: `app/assets/sass/main.scss`

**Structure**:
```scss
// Import GOVUK Toolkit
@import "govuk-prototype-kit/styles/govuk-frontend-toolkit";
@import "govuk-prototype-kit/styles/govuk-prototype-components";

// Your custom styles
@import "custom-styles";
```

### JavaScript

JavaScript files are loaded on every page by default.

**Location**: `app/assets/javascripts/`

**Structure**:
```javascript
// app/assets/javascripts/application.js
// Main application JavaScript

// Use window.APP_NAME pattern to avoid conflicts
window.SERVICE_NAME = window.SERVICE_NAME || {};

window.SERVICE_NAME.init = function() {
  // Your init code
};
```

### Plugins Asset Structure

When creating plugins, assets are made available at:
- `/plugin-assets/<plugin-name>/<asset-path>`

For Sass in plugins, use the `$govuk-plugins-url-context` variable for URLs.

## Best Practices

- **Namespacing**: Always namespace your CSS classes and JavaScript variables
  ```scss
  .service-name_component { ... }
  ```

- **Sass Variables**: Use your service name as a prefix for custom variables
  ```scss
  $service-name-primary-color: #000;
  ```

- **JavaScript Module Pattern**: Wrap code in IIFEs or use module patterns
  ```javascript
  (function() {
    // Your code
  })();
  ```

## File Locations

```
app/
├── assets/
│   ├── images/          # Images used in the prototype
│   ├── javascripts/     # JavaScript files
│   │   └── application.js
│   └── sass/
│       └── main.scss    # Main Sass entry point
```
