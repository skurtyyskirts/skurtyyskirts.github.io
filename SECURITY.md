# Security Policy

`skurtyyskirts.com` is a static portfolio site served by GitHub Pages. It has
no backend, no database, no authentication, and stores no visitor data. The
entire page is self-contained: all scripts, styles, fonts and images are
inlined or decoded from an embedded bundle into `blob:` URLs at runtime, so the
site makes no third-party network requests.

## Reporting a Vulnerability

If you believe you have found a security issue, please email
**hi@skurtyyskirts.com**. Machine-readable contact details are also published
at [`/.well-known/security.txt`](.well-known/security.txt).

Please include:

- A description of the issue and its potential impact
- Steps to reproduce (a proof of concept if possible)
- Any relevant URLs, requests, or screenshots

Please do not open a public GitHub issue for security reports.

## Hardening in place

- **Content-Security-Policy** (meta tag in `index.html`) restricts every
  resource type to `'self'` and `blob:`. There are no allowances for external
  origins, which blocks external script injection and data exfiltration.
  `object-src 'none'`, `base-uri 'self'`, `form-action 'self'`, and
  `frame-ancestors 'self'` are set as defense in depth.
- **Referrer-Policy** is set to `strict-origin-when-cross-origin`.
- **No third-party requests**: fonts are bundled locally rather than loaded from
  Google Fonts, so no visitor IP/referrer data leaks to external services.
- **No secrets**: the repository and the published bundle contain no API keys,
  tokens, or credentials. The only contact address (`hi@skurtyyskirts.com`) is
  published intentionally.
