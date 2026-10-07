# Plugins

## Overview

The GOVUK Prototype Kit supports plugins that can extend functionality across services. Plugins can add Nunjucks macros, assets, templates, and more.

## Plugin Configuration

Plugins require a `govuk-prototype-kit.config.json` file at their root.

**Basic structure**:
```json
{
  "name": "service-name",
  "version": "1.0.0",
  "assets": ["/assets/"],
  "scripts": ["/javascripts/app.js"]
}
```

## Config File Options

### assets
Paths for files to make available at `/plugin-assets/<name>/<path>`:
```json
{
  "assets": ["/assets/", "/images/profile.png"]
}
```

### importNunjucksMacrosInto
Layout files to import Nunjucks macros into:
```json
{
  "importNunjucksMacrosInto": ["/nunjucks/layouts/main.njk"]
}
```

### nunjucksFilters
Nunjucks filter files:
```json
{
  "nunjucksFilters": ["/filters.js"]
}
```

### nunjucksPaths
Paths for Nunjucks includes, layouts, and macros:
```json
{
  "nunjucksPaths": ["/nunjucks"]
}
```

### nunjucksMacros
Named Nunjucks macros:
```json
{
  "nunjucksPaths": ["/nunjucks"],
  "nunjucksMacros": [
    {
      "macroName": "serviceTextInput",
      "importFrom": "service/macros/text-input.njk"
    }
  ]
}
```

### pluginDependencies
Other plugins this plugin depends on:
```json
{
  "pluginDependencies": ["govuk-frontend"]
}
```

### sass
Sass files to compile:
```json
{
  "sass": ["/styles.scss"]
}
```

### scripts
JavaScript files to load:
```json
{
  "scripts": ["/scripts.js"]
}
```

### stylesheets
CSS files to load:
```json
{
  "stylesheets": ["/styles.css"]
}
```

### templates
Pre-built templates:
```json
{
  "templates": [
    {
      "path": "/templates/hello-world.njk",
      "name": "Hello world page",
      "type": "nunjucks"
    }
  ]
}
```

## Plugin Development Best Practices

1. **Use a namespace**: Choose a short, unique name to avoid conflicts
2. **Prefix everything**: Use namespace prefix for CSS classes, JS variables, and macros
3. **Test compatibility**: Ensure plugins work together
4. **Document dependencies**: List required plugins and versions

## Installing Plugins

Plugins can be installed via the Prototype Kit's plugin manager or manually:

**Manual installation**:
1. Copy plugin folder to `node_modules/`
2. Add plugin name to `package.json` dependencies
3. Run `npm install`

## File Location

```
project-root/
├── node_modules/
│   └── plugin-name/
│       ├── govuk-prototype-kit.config.json
│       ├── package.json
│       └── ...
```
