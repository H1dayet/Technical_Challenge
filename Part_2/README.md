# Saucedemo Login Tests

Playwright tests for the login functionality on saucedemo.com

## Setup

Make sure you have Node.js installed (v16+), then run:

```bash
npm install
```

This installs Playwright, TypeScript, and the browser binaries needed to run tests.

## Running Tests

```bash
npx playwright test                # run all tests
npx playwright test --headed       # see the browser while tests run
npx playwright test --ui           # interactive mode
npx playwright show-report         # view test results
```

## What's tested

- Login with valid credentials (standard_user)
- Login with invalid credentials - checks error message
- Trying to login with empty username/password fields

## Files

- `pages/LoginPage.ts` - page object with locators and methods
- `tests/login.spec.ts` - the actual test cases
- `playwright.config.ts` - test config (timeout, base URL, etc)
