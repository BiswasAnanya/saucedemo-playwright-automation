# SauceDemo Playwright Automation

Automation project covering the SauceDemo smoke test suite, built with Playwright and TypeScript. This is a companion project to [`saucedemo-manual-testing`](https://github.com/BiswasAnanya/saucedemo-manual-testing), a manual QA project covering 80 test cases across 8 feature-based suites for [SauceDemo](https://www.saucedemo.com).

## Purpose

This project automates the 10-case smoke suite from the manual project, the critical path through Login → Browse Products → Add to Cart → Checkout → Order Confirmation, plus logout.

Full scope and rationale: see [`automation-plan.md`](./automation-plan.md).

## Status

🚧 In progress. Currently implementing `SMK-001` (login).

| Item | Status |
|---|---|
| Playwright + TypeScript initialized | ✅ Done |
| Page Object folder structure | ✅ Done |
| `LoginPage.ts` | ✅ Done |
| SMK-001 – Login with valid credentials | 🔄 In progress |
| SMK-002 – SMK-010 | ⬜ Not started |

Progress is tracked via [GitHub Issues](../../issues) and the [`SauceDemo Smoke Automation`](../../projects) board.

## Tech Stack

- [Playwright](https://playwright.dev/) with TypeScript
- Chromium only (Firefox/WebKit disabled for this project)
- Page Object Model pattern, using `data-test` attributes as the primary locator strategy


## Running the Tests

```bash
npm install
npx playwright test
```

View the HTML report after a run:

```bash
npx playwright show-report
```

## Traceability

Each automated test maps to a smoke case in the manual suite. Full mapping in [`automation-plan.md`](./automation-plan.md).

## Related Repository

- [`saucedemo-manual-testing`](https://github.com/BiswasAnanya/saucedemo-manual-testing), full manual test plan, 8 feature suites, bug reports, and requirements traceability matrix.
