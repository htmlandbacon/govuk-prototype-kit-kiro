# Testing and User Research

## Overview

The GOVUK Prototype Kit is designed for rapid iteration based on user feedback. Testing is integral to the service design process.

## Running the Prototype

**Start the server**:
```bash
npm start
```

The prototype runs at `http://localhost:3000`

**Production mode**:
```bash
npm run serve
```

## Testing with Users

### Setting Up for User Research

1. **Password protection**: When running online, set a password to prevent accidental public access
2. **Environment variables**:
   - `NODE_ENV=production`
   - `PASSWORD=your-password`

### Using the Prototype Kit Features

- **Clear data**: Use the "Clear data" link in the footer between user sessions
- **Default data**: Set default values in `app/data/session-data-defaults.js` for consistent testing scenarios

## Data Management

### Clearing Data

- **In-browser**: Click "Clear data" in the footer
- **Programmatically**: Use links to clear specific data
- **At start of session**: Use default data file

### Testing Scenarios

Create links to set up different user scenarios:
```html
<!-- Test returning user -->
<a href="/start?first-name=Amina&over-18=yes">Test returning user</a>

<!-- Test new user -->
<a href="/start">Test new user</a>
```

## Accessibility Testing

### Tools

- **WAVE**: Browser extension for accessibility evaluation
- **axe**: Automated accessibility testing
- **Screen readers**: NVDA, VoiceOver, JAWS

### Key Checks

1. **Headings**: One H1 per page, nested correctly
2. **Form labels**: All inputs have associated labels
3. **Focus indicators**: Visible focus on interactive elements
4. **Color contrast**: Sufficient contrast between text and background
5. **Alt text**: All images have descriptive alt text

## Cross-Browser Testing

Test in:
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers

## Mobile Testing

Use browser developer tools to test responsive design:
- iPhone SE
- iPhone 12/13
- Pixel 5
- Tablet sizes

## Best Practices

1. **Test early and often**: Run user research throughout the design process
2. **Record sessions**: With consent, record user research sessions
3. **Test tasks, not features**: Focus on user goals, not specific functionality
4. **Iterate based on feedback**: Make changes and re-test
5. **Document findings**: Keep a record of what was tested and what was learned
