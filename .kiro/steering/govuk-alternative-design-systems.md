# Alternative Design Systems

## Overview

While the GOVUK Design System is the standard for UK government services, there are alternative design systems available for specific contexts. This guide covers using alternative design systems like the DWP (Department for Work and Pensions) Design System within a GOVUK Prototype Kit project.

## When to Use Alternative Design Systems

### DWP Design System
The DWP Design System is designed for departments and agencies across the UK government. Consider using it when:

- Building services specifically for DWP or its agencies
- Working on cross-government services that need DWP styling
- You need DWP-specific patterns and components
- Your team is already familiar with the DWP system

### Other Design Systems
- **USWDS** (United States Design System) - For US federal services
- **Design System UK** - Alternative UK government design system
- **ONS Design System** - Office for National Statistics patterns
- **HMRC Design System** - Her Majesty's Revenue and Customs patterns

## Installing DWP Design System

### As a GOVUK Prototype Kit Plugin

Recent versions of the GOVUK Prototype Kit support installing DWP frontend as a plugin:

```bash
npm install @dwp/dwp-frontend
```

### Manual Installation

If not using the Prototype Kit's plugin system:

1. Install the package:
```bash
npm install @dwp/dwp-frontend
```

2. Configure your project to include DWP styles:
```scss
// app/assets/sass/main.scss
@import "node_modules/@dwp/dwp-frontend/styles/main";
```

3. Include DWP JavaScript:
```javascript
// app/assets/javascripts/application.js
import '@dwp/dwp-frontend/dist/dwp-frontend.min.js';
```

## Using DWP Components

### DWP Component Packages

The DWP design system provides components in multiple frameworks:

- **styles/theme** - Framework agnostic theme and styles
- **components/react** - React component implementations

### Basic Component Structure

DWP components follow similar patterns to GOVUK components:

```html
<div class="dwp-field-group">
  <label class="dwp-label" for="example">
    Example label
  </label>
  <input class="dwp-input" id="example" name="example" type="text">
</div>

<button class="dwp-button">
  Submit
</button>
```

## Mixing Design Systems

### When to Mix
Consider mixing design systems when:

- Migrating from GOVUK to DWP (or vice versa)
- Integrating legacy components
- Gradually transitioning to a new design system

### Challenges
- **Inconsistent styling** - Different visual languages
- **Maintenance overhead** - Two codebases to maintain
- **Accessibility testing** - Need to verify both systems

### Best Practices
1. **Keep it minimal** - Don't mix on the same page unless necessary
2. **Namespace styles** - Use CSS custom properties or BEM naming
3. **Document decisions** - Record why certain components use different systems
4. **Test thoroughly** - Ensure consistency in behavior and accessibility

## Custom Layouts for Agents

When building agent interfaces, consider these layout patterns:

### Agent Dashboard Layout

```html
<div class="dwp-grid-row">
  <div class="dwp-grid-column-one-quarter">
    <!-- Agent navigation -->
  </div>
  <div class="dwp-grid-column-three-quarters">
    <!-- Main agent interface -->
  </div>
</div>
```

### Agent Conversation Interface

```html
<div class="dwp-agent-panel">
  <div class="dwp-agent-messages">
    <!-- Chat messages -->
  </div>
  <div class="dwp-agent-input">
    <!-- Input field -->
  </div>
</div>
```

### Custom Styles for Agent Interfaces

```scss
// app/assets/sass/_agent-interfaces.scss
.dwp-agent-panel {
  border: 1px solid #b1b4b6;
  border-radius: 4px;
  margin-top: 20px;
  
  .dwp-agent-messages {
    max-height: 500px;
    overflow-y: auto;
    padding: 20px;
  }
  
  .dwp-agent-input {
    border-top: 1px solid #b1b4b6;
    padding: 15px;
  }
}
```

## Accessibility Considerations

When using alternative design systems:

1. **Verify accessibility** - Ensure all components meet WCAG 2.1 AA standards
2. **Test with assistive technologies** - Use screen readers and keyboard navigation
3. **Check contrast ratios** - DWP colors should meet 4.5:1 text contrast
4. **Validate ARIA** - Ensure proper ARIA attributes are in place

## Migration Guide

### From GOVUK to DWP

1. **Audit your components** - List all GOVUK components in use
2. **Map to DWP equivalents** - Find corresponding DWP components
3. **Update templates** - Replace GOVUK macros with DWP equivalents
4. **Update styling** - Switch from GOVUK to DWP SCSS imports
5. **Test thoroughly** - Verify all functionality and accessibility

### From DWP to GOVUK

1. **Install GOVUK Frontend** - `npm install govuk-frontend`
2. **Update imports** - Switch SCSS imports to GOVUK
3. **Update templates** - Replace DWP classes with GOVUK classes
4. **Update JavaScript** - Use GOVUK Frontend JavaScript modules
5. **Test thoroughly** - Verify all functionality

## Resources

- [DWP Design System GitHub](https://github.com/dwp/design-system)
- [DWP Components on NPM](https://www.npmjs.com/package/@dwp/dwp-frontend)
- [DWP Components Repository](https://github.com/dwp/dwp-components)
- [GOVUK Design System](https://design-system.service.gov.uk/)
- [GOVUK Prototype Kit Plugins](https://github.com/alphagov/govuk-prototype-kit#plugins)

## References

- [DWP Design System on npm](https://www.npmjs.com/package/@dwp/dwp-frontend)
- [GOVUK Prototype Kit Plugin Architecture](https://github.com/alphagov/govuk-prototype-kit#plugins)