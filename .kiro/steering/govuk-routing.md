# Routing

## Overview

Routing in the GOVUK Prototype Kit determines what happens when users visit or submit forms to different URLs. Routes are defined in `app/routes.js`.

## Basic Route Structure

```javascript
// GET route
router.get('/page-name', function(req, res) {
  res.render('page-name');
});

// POST route (for form submissions)
router.post('/page-name', function(req, res) {
  // Process form data
  res.redirect('/next-page');
});
```

## Auto Routing

The Prototype Kit supports automatic page routing. Pages created in the `app/views/` folder are automatically accessible at `/page-name` without requiring explicit route definitions.

**Example**:
- File: `app/views/mypage.html`
- Accessible at: `http://localhost:3000/mypage`

## Data Persistence

Form data is stored in `req.session.data`. The name attribute of form inputs determines the storage key.

```javascript
// Access form data
var firstName = req.session.data['first-name'];

// Store data directly
req.session.data['answer'] = 'value';
```

## Branching Journeys

Use routing to send users down different paths based on their answers.

```javascript
router.post('/answer', function(req, res) {
  var answer = req.session.data['question'];
  
  if (answer === 'yes') {
    res.redirect('/yes-path');
  } else {
    res.redirect('/no-path');
  }
});
```

## Advanced Branching (Checkboxes)

For checkboxes, check if an answer is in the array:

```javascript
var exports = req.session.data['exports'];

if (exports.includes("Fruit")) {
  res.redirect("/fruit-questions");
} else {
  res.redirect("/next-question");
}
```

To check for an exact match:

```javascript
const util = require('util');

if (util.deepStrictEqual(exports, ['Fruit'])) {
  res.redirect("/fruit-questions");
}
```

## Setting Data via Links

You can set data directly in links for testing different scenarios:

```html
<!-- Set data -->
<a href="/start?first-name=Amina">Start</a>

<!-- Clear data -->
<a href="/start?first-name">Start</a>

<!-- Set multiple pieces of data -->
<a href="/start?first-name=Amina&over-18=yes">Start</a>
```

## File Location

```
app/
└── routes.js    # Main routes file
```

## Best Practices

1. **Consistent naming**: Use hyphens for multi-word route names
2. **POST for forms**: Always use POST routes for form submissions
3. **Redirect after POST**: Follow PRG pattern (Post-Redirect-Get)
4. **Test branching logic**: Verify all journey paths work correctly
