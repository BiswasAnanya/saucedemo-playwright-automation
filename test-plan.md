# Automation Plan - SauceDemo Smoke Suite

## Scope

Automates the 10 smoke test cases (SMK-001–SMK-010) defined in `saucedemo-manual-testing/04-smoke-testing/smoke-test-suite.md`. 
These smoke tests will be used for regression purpose.

Out of scope: negative/invalid input cases, special users (`problem_user`, `error_user`, etc.), visual regression, cross-browser execution, and API testing.

## Stack

| Item | Detail |
|---|---|
| Framework | Playwright Test |
| Language | TypeScript |
| Browser | Chromium only |
| Base URL | `https://www.saucedemo.com` |
| Pattern | Page Object Model, `data-test` attributes as primary locator strategy |

## Traceability

| Automated Test | Smoke Case | Manual Test Case |
|---|---|---|
| Login with valid credentials | SMK-001 | TC-001 |
| Inventory page loads after login | SMK-002 | TC-101 |
| Add single product to cart | SMK-003 | TC-301 |
| Add multiple products to cart | SMK-004 | TC-302 |
| Checkout Step One accessible | SMK-005 | TC-401 |
| Proceed from Checkout Step One | SMK-006 | TC-403 |
| Checkout Overview loads correctly | SMK-007 | TC-501 |
| Order completion | SMK-008 | TC-510 |
| Cart emptied after order completion | SMK-009 | TC-606 |
| Successful logout | SMK-010 | TC-702 |

## Known Defects

Where a smoke case overlaps a defect logged in `saucedemo-manual-testing/05-bug-reports`, the test either documents the defect ID and asserts current (defective) behavior, or is marked `test.fail()` with the defect ID referenced, until resolved.
