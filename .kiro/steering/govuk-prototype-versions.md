# Prototype Versions and Design Histories

## Overview

Versioning allows you to maintain multiple iterations of your prototype without affecting previous versions. This is particularly useful for:

- **User research** — Keep an older version live while testing a new one
- **Stakeholder feedback** — Compare multiple versions side-by-side to collaborate more effectively
- **Incremental changes** — Modify and improve designs easily without breaking existing functionality

## Why Version Your Prototype

Maintaining a version history enables:

- **Parallel testing** — Test multiple design directions with different user groups
- **Rollback capability** — Quickly revert to a previous version if issues are discovered
- **Change tracking** — Document and communicate what changed and why between versions
- **Collaboration** — Different team members can work on different versions simultaneously

## Folder Structure

```
project-root/
├── app/
│   ├── routes.js
│   └── views/
│       ├── v1/
│       │   ├── routing.js
│       │   ├── question-1.html
│       │   ├── question-2.html
│       │   └── nested/
│       │       ├── question-1.html
│       │       └── question-2.html
│       └── v2/
│           ├── routing.js
│           ├── question-1.html
│           └── question-2.html
```

### Key Files

- **routes.js** — Central routing file that mounts each version's router under its respective path (e.g., `/v1`, `/v2`)
- **routing.js** — Version-specific files that define routes and ensure navigation stays within the correct version

## Setting Up Versions

### Version-Agnostic Forms

HTML forms should NOT have hardcoded action attributes:

```html
<form method="post" novalidate>
  <h1 class="govuk-heading-xl">Question 1</h1>
  <button type="submit" class="govuk-button" data-module="govuk-button">
    Continue
  </button>
</form>
```

### Automatic Redirects

Add this code to each version's `routing.js` to ensure redirects always include the correct version prefix:

```javascript
module.exports = () => {
  const govukPrototypeKit = require('govuk-prototype-kit');
  const subRouter = govukPrototypeKit.requests.setupRouter();

  subRouter.use((req, res, next) => {
    const originalRedirect = res.redirect;
    res.redirect = function(url) {
      if (url.startsWith('/') && !url.startsWith(req.baseUrl)) {
        url = req.baseUrl + url;
      }
      return originalRedirect.call(this, url);
    };
    next();
  });

  subRouter.post('/question-1', (req, res) => {
    res.redirect('/question-2');
  });

  return subRouter;
};
```

**Important:** Type out the full path for pages (e.g., `/question-1` or `/question-2`). Do not include `v1` or `v2` in the redirect — this is handled automatically. For nested subdirectories, include the full path (e.g., `/nested/question-1`).

### Mounting Version Routers

In `app/routes.js`, mount each version's router:

```javascript
const govukPrototypeKit = require('govuk-prototype-kit');
const router = govukPrototypeKit.requests.setupRouter();

router.use('/v1', require('./views/v1/routing')());
router.use('/v2', require('./views/v2/routing')());

module.exports = router;
```

## Creating a New Version

1. **Duplicate the latest version folder** — Copy `v2` and rename to `v3`. This creates a copy of all pages and routes.

2. **Mount the new version** — Add to `routes.js`:
   ```javascript
   router.use('/v3', require('./views/v3/routing')());
   ```

3. **Make your changes** — Edit files in the `v3` folder without affecting previous versions.

## Managing Design Histories

### Version Index

Keep an index page that documents each version:

```html
<h1 class="govuk-heading-xl">Prototype Versions</h1>

<ul class="govuk-list">
  <li><a href="/v1">Version 1 — Initial concept</a></li>
  <li><a href="/v2">Version 2 — Based on round 1 research findings</a></li>
  <li><a href="/v3">Version 3 — Iteration after round 2 research</a></li>
</ul>
```

### Changelog Format

Consider maintaining a changelog that documents:

- Version number and date
- Research cycle or feedback source
- Key changes made
- Reason for changes
- Any known issues or limitations

```
## Version 3 (2024-01-15)
- **Round 3 research iteration**
- Changed question wording based on user comprehension issues in V2
- Added confirmation page after submission
- Removed optional field from address form

## Version 2 (2023-12-01)
- **Round 2 research iteration**
- Simplified start page
- Added progress indicator
- Fixed navigation flow issues from V1
```

## Best Practices

1. **Consistent naming** — Use semantic version numbers (v1, v2, v3) or date-based naming (v2024-01)
2. **Document changes** — Keep a changelog or index that explains what changed between versions
3. **Isolate changes** — Each version should be fully self-contained
4. **Archive old versions** — Don't delete previous versions; keep them for reference and comparison
5. **Mark current version** — Clearly indicate which version is the current one for testing
6. **Version-agnostic forms** — Always omit the action attribute from forms
7. **Automatic redirects** — Use the redirect wrapper pattern in every version's routing.js

## Reference

[GOV.UK Prototype Kit Versioning](https://design.tax.service.gov.uk/prototype-guidance/setting-up-different-versions-of-your-prototype/)