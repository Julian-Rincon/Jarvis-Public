# Security

## Public Release Policy

This repository is intentionally documentation-only.

The private project contains material that should not be exposed in a public repository, including:

- local environment assumptions
- personal workflow context
- private configuration
- local automation details tied to a real workstation
- API and OAuth integration setup

## Why the Source Is Not Public

The goal of this repository is to demonstrate technical depth without giving away the implementation or exposing sensitive data.

This is both a security choice and an ownership choice:

- security, because the real project touches personal and operational context
- ownership, because the implementation reflects substantial original effort

## Publishing Guidelines

If demo material is added to this repository:

- remove usernames, email addresses, device names, and file paths
- avoid screenshots showing inboxes, calendars, or personal reminders
- never include `.env`, `token.json`, `credentials.json`, or machine-specific logs
- never publish API keys, bot tokens, or model endpoints that are not meant to be public

## Recommended Portfolio Practice

For portfolio review, prefer:

- architecture diagrams
- feature summaries
- sanitized screenshots
- live walkthroughs
- recorded demos with redacted content

Avoid:

- publishing operational prompts
- publishing automation internals that can be trivially cloned
- publishing private datasets or user profile artifacts
