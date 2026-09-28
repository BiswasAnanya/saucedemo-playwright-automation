# Automation Plan - SauceDemo Smoke Suite

This document defines the scope, approach, and structure for automating the SauceDemo smoke test suite using Playwright and TypeScript. It serves as the automation counterpart to the manual test plan maintained in the `saucedemo-manual-testing` repository.

The purpose of this project is to establish a fast, repeatable regression check covering the application's critical user journey.

## Scope

- Automates the 10 smoke test cases (SMK-001–SMK-010) defined in `saucedemo-manual-testing/04-smoke-testing/smoke-test-suite.md`.
- Coverage of the primary customer journey: Login → Browse Products → Add to Cart → Checkout → Order Confirmation, plus logout.

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

## Structure

- **Page Object Model** is used throughout. Each page in the user journey (Login, Inventory, Cart, Checkout Step One, Checkout Step Two, Checkout Complete) has its own class containing locators and the actions available on that page. Test files contain assertions and orchestration only — no raw selectors.
- **Selector strategy**: `data-test` attributes are used as the primary locator strategy, as SauceDemo provides stable, purpose-built test hooks. `id` is used as a fallback only where `data-test` is unavailable.
- **Test independence**: each test is written to set up its own required state (e.g., logging in, adding items to cart) rather than depending on execution order or shared state from a previous test, in line with Playwright's parallel execution model.

## Known Defects

Where a smoke case overlaps a defect logged in `saucedemo-manual-testing/05-bug-reports`, the test either documents the defect ID and asserts current (defective) behavior, or is marked `test.fail()` with the defect ID referenced, until resolved.
