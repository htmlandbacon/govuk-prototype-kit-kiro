# Project Structure

## Overview

Understanding the GOVUK Prototype Kit project structure is essential for maintaining consistency across services.

## Directory Structure

```
project-root/
├── app/
│   ├── assets/
│   │   ├── images/
│   │   ├── javascripts/
│   │   │   └── application.js
│   │   └── sass/
│   │       └── main.scss
│   ├── data/
│   │   └── session-data-defaults.js
│   ├── views/
│   │   ├── layouts/
│   │   │   └── main.html
│   │   ├── index.html
│   │   ├── start.html
│   │   └── [page-name].html
│   └── routes.js
├── node_modules/
├── public/
│   └── styles/
│       └── main.css
├── .env
├── .gitignore
├── package.json
├── server.js
└── govuk-prototype-kit.config.json
```

## Key Files and Directories

### app/

**Contents**: Application code
- `assets/` - Static assets (images, JavaScript, Sass)
- `data/` - Session data defaults
- `views/` - Templates and layouts
- `routes.js` - Route definitions

### app/assets/

**Contents**: Static resources

**images/** - Images used in the prototype
**javascripts/** - JavaScript files (compiled into application.js)
**sass/** - Sass source files (compiled to CSS)

### app/data/

**Contents**: Default session data

**session-data-defaults.js** - JavaScript module exporting default values for form fields

```javascript
module.exports = {
  'first-name': 'John',
  'last-name': 'Doe'
}
```

### app/views/

**Contents**: Nunjucks templates

**layouts/main.html** - Main layout file, extended by all pages
**[page-name].html** - Individual pages (auto-routed)

### app/routes.js

**Contents**: Express route definitions

```javascript
router.get('/page', function(req, res) {
  res.render('page');
});

router.post('/submit', function(req, res) {
  // Process form
  res.redirect('/next-page');
});
```

### node_modules/

**Contents**: NPM dependencies (not committed to git)

### public/

**Contents**: Static files served directly
- `styles/main.css` - Compiled CSS

### .env

**Contents**: Environment variables (not committed)

```
PASSWORD=secret123
NODE_ENV=development
```

### package.json

**Contents**: NPM package configuration

### server.js

**Contents**: Application entry point

### govuk-prototype-kit.config.json

**Contents**: Plugin configuration (if this is a plugin)

## Plugin Structure

```
plugin/
├── govuk-prototype-kit.config.json
├── package.json
├── assets/
├── javascripts/
├── sass/
├── nunjucks/
└── templates/
```

## Best Practices

1. **Consistent structure** - Keep all services using the same structure
2. **Clear naming** - Use hyphens for multi-word names
3. **Document custom additions** - Note any non-standard files
4. **Version control** - Commit all source files, ignore node_modules
5. **Environment files** - Never commit `.env` files with secrets
