# Security and Privacy

## Overview

Prototypes created with the GOVUK Prototype Kit look like live services but do not have the same security provisions. Security considerations are essential when testing with real or simulated user data.

## Key Principles

### prototypes Are NOT Live Services

- Do not use real user data without proper consent and protection
- Prototypes lack production-grade security
- Always password-protect online prototypes
- Make it clear to users this is a prototype

### Data Protection

- **Consent**: Always get consent before collecting user data
- **Anonymise**: Use fake data where possible
- **Minimise**: Collect only the data you need for testing
- **Secure storage**: Protect any recorded data
- **Right to be forgotten**: Allow data deletion

## Password Protection

### Setting a Password (Production)

When publishing online, set environment variables:

```bash
NODE_ENV=production
PASSWORD=your-secure-password
USERNAME=admin  # Optional, required for older versions
```

### Multiple Passwords

For temporary access (v13.15.0+):

```bash
PASSWORD_KEYS=PASSWORD_01,PASSWORD_02
PASSWORD_01=temp-password-1
PASSWORD_02=temp-password-2
```

## Handling Sensitive Data

### What NOT to Do

- Don't store sensitive data in session storage
- Don't log sensitive user information
- Don't use real personal data without proper safeguards
- Don't deploy prototypes to public servers without password protection

### What to Do Instead

- Use synthetic/test data
- Anonymise data where possible
- Use GOVUK Notify for email (with proper setup)
- Implement data deletion features

## Hosting Considerations

### Safe Hosting

- Any Node.js hosting service (Heroku, Render, Railway)
- Do NOT use static hosting (GitHub Pages, Netlify) - requires backend

### Security Checklist

- [ ] Password protection enabled
- [ ] No real user data
- [ ] No API keys in code
- [ ] HTTPS enabled (use hosting service's certificate)
- [ ] Privacy notice provided
- [ ] Data deletion mechanism available

## Environment Variables

### Recommended .gitignore

```
.env
node_modules/
.app/
```

### Never Commit

- `.env` files
- API keys
- Real user data
- Sensitive configuration

## GOV.UK Notify API Keys

When using GOV.UK Notify:

1. Save keys in `.env` file (not committed)
2. Revoke keys immediately if exposed
3. Use different keys for development and production
4. Never expose keys in client-side code

## Privacy Notices

Provide a privacy notice for users who interact with your prototype, especially if collecting personal data. Use the GOVUK Prototype Kit privacy notice as a template.

## User Consent

For user research:

1. Explain the prototype is for testing
2. Get consent before recording
3. Explain how data will be used
4. Allow data withdrawal at any time
5. Provide contact information

## Best Practices

1. **Assume all data is visible** - Session data is stored client-side
2. **Clear data between users** - Use the footer link or programmatically
3. **Test with realistic but safe data** - Use synthetic datasets
4. **Document security decisions** - Keep a security log
5. **Get security review** - Have someone else review your setup
