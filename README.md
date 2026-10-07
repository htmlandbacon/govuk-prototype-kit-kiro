# KIRO Prototype

A [GOVUK Prototype Kit](https://govuk-prototype-kit.herokuapp.com/) based prototype built to test and demonstrate features within the KIRO development environment.

## Overview

This project uses the GOVUK Prototype Kit as a foundation to explore how the KIRO IDE and its agent capabilities can be integrated with government digital services prototyping workflows.

## Features

- **GOVUK Design System compliance** - Built using the GOVUK Frontend framework
- **Agent-driven development** - Utilizes KIRO's autonomous coding capabilities
- **Modular architecture** - Supports plugins for extended functionality
- **Accessibility first** - All components follow GOVUK accessibility standards
- **Multiple prototype versions** - Support for versioning and design history tracking
- **Alternative design systems** - Guidance on using DWP and other design systems

## Getting Started

### Prerequisites

- Node.js (v18 or higher)
- npm or yarn

### Installation

1. Clone this repository
   ```bash
   git clone <repository-url>
   cd kiro-prototype
   ```

2. Install dependencies
   ```bash
   npm install
   ```

3. Run the prototype
   ```bash
   npm start
   ```

4. Open your browser to `http://localhost:3000`

## Using This as a Template

This repository is designed to be used as a **template** for new GOVUK Prototype Kit projects. To create a new project:

### Option 1: Use GitHub's Template Feature

1. Click "Use this template" on this repository
2. Name your new repository
3. Clone and start building

### Option 2: Manual Template Setup

```bash
# Clone this repository
git clone https://github.com/htmlandbacon/govuk-prototype-kit-kiro.git my-project
cd my-project

# Remove the existing git history
rm -rf .git

# Initialize a new repository
git init
git remote add origin git@github.com:your-org/my-project.git

# Add your files and commit
git add .
git commit -m "Initial commit from kiro-prototype template"

# Push to your new repository
git push -u origin main
```

## Project Structure

See the [project structure documentation](.kiro/steering/govuk-project-structure.md) for details.

```
├── app/
│   ├── assets/           # Images, JavaScript, Sass
│   ├── data/             # Session data defaults
│   ├── views/            # Nunjucks templates
│   └── routes.js         # Route definitions
├── public/               # Static files
├── node_modules/         # Dependencies
└── .kiro/                # KIRO configuration and steering files
```

## Development

### Running in development mode

```bash
npm run dev
```

### Running tests

```bash
npm test
```

## Documentation

- [GOVUK Prototype Kit Overview](.kiro/steering/govuk-prototype-kit-overview.md)
- [Project Structure](.kiro/steering/govuk-project-structure.md)
- [Assets (Sass, JavaScript, CSS)](.kiro/steering/govuk-assets.md)
- [Plugins](.kiro/steering/govuk-plugins.md)
- [Layouts](.kiro/steering/govuk-layouts.md)
- [Routing](.kiro/steering/govuk-routing.md)
- [Nunjucks](.kiro/steering/govuk-nunjucks.md)
- [Security](.kiro/steering/govuk-security.md)
- [Testing](.kiro/steering/govuk-testing.md)
- [Prototype Versions](.kiro/steering/govuk-prototype-versions.md) - Manage multiple prototype versions for user research and iteration
- [Alternative Design Systems](.kiro/steering/govuk-alternative-design-systems.md) - Use DWP and other design systems in your prototypes

## KIRO Agent Hooks

This project uses KIRO agent hooks for automated development workflows. See `.kiro/hooks/` for available hooks.

## License

Unless otherwise stated, this code is available under the [MIT License](LICENSE).
