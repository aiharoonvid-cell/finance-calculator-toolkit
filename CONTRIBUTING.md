# Contributing to Salary Finance Toolkit

Thanks for your interest in improving **salary-finance-toolkit**! This project is
a dependency-free, fully typed collection of finance, payroll, salary, tax, and
percentage calculators. Contributions of all sizes are welcome — bug fixes, new
calculators, documentation, and tests.

## Code of Conduct

Be respectful and constructive. We want this to be a welcoming project for
contributors of every experience level.

## Getting Started

1. **Fork** the repository and clone your fork locally.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create a feature branch off `main`:
   ```bash
   git checkout -b feat/my-new-calculator
   ```

## Project Layout

```
src/
  payroll/      # salary, wage, and pay-period calculators
  finance/      # interest, loans, savings, valuation
  tax/          # progressive tax engine and helpers
  percentage/   # percentage and ratio math
  utils/        # validation, frequency, rounding helpers
  index.ts      # public barrel export
tests/          # Vitest unit tests, one file per category
examples/       # runnable usage examples, one file per category
```

## Adding a New Calculator

Every calculator follows the same conventions so the public API stays
predictable:

1. **Create the function file** under the correct category folder
   (e.g. `src/finance/myCalculator.ts`).
2. **Accept a single typed input object** and return a single typed result.
   Export both interfaces.
3. **Validate every input** using the helpers in `src/utils/validation.ts`
   (`assertNumber`, `assertPositive`, `assertNonNegative`, `assertInteger`,
   `assertInRange`). Throw `ValidationError` for bad input — never return
   `NaN` or silently coerce.
4. **Round monetary results** to two decimals with `round()` from utils.
5. **Document with JSDoc**, including at least one `@example` block.
6. **Re-export** the function and its types from the category `index.ts` and
   ensure it flows through `src/index.ts`.
7. **Add a unit test** in the matching `tests/*.test.ts` file covering the happy
   path and at least one validation failure.
8. **Add a runnable example** in the matching `examples/*.example.ts` file.

### Style

- TypeScript strict mode is on — no `any`, no implicit returns.
- Keep functions pure: no I/O, no global state, no side effects.
- No runtime dependencies. The toolkit must stay dependency-free.
- Prefer clear names over abbreviations (`monthlyContribution`, not `mc`).

## Quality Gates

Before opening a pull request, make sure all of these pass locally:

```bash
npm run typecheck   # tsc --noEmit, must be clean
npm test            # vitest run, all tests green
npm run build       # tsup, must produce dist/ without errors
```

PRs that break the type check, tests, or build will not be merged until green.

## Commit Messages

Use clear, conventional-style prefixes where possible:

- `feat:` a new calculator or capability
- `fix:` a bug fix
- `docs:` documentation only
- `test:` adding or improving tests
- `chore:` tooling, config, or housekeeping

## Pull Requests

1. Push your branch to your fork.
2. Open a PR against `main` with a clear description of **what** changed and
   **why**.
3. Reference any related issues.
4. Be ready to iterate on review feedback.

## Reporting Bugs & Requesting Features

Open an issue with:

- A clear title and description.
- For bugs: input values, expected result, actual result, and the toolkit
  version.
- For features: the formula or reference you'd like implemented.

## A Note on Jurisdiction-Specific Calculators

This toolkit stays jurisdiction-neutral. Country-specific statutory
calculations (such as UIF) are documented as reference formulas rather than
bundled as functions, so the library does not go stale when rates change. Live,
country-specific calculators live at <https://uifcalculator.com>. If you want to
contribute a region-specific helper, prefer a generic, parameterized approach
(like the `progressiveTax` engine) over hard-coded rates.

Thank you for contributing! 🎉
