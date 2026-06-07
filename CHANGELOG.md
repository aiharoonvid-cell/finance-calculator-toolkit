# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2026-06-07

### Added

- Initial public release of **salary-finance-toolkit**.
- **Payroll** calculators: `grossToNet`, `netToGross`, `hourlyWage`,
  `overtimePay`, `annualSalary`, `proRataSalary`, `payPeriodSalary`.
- **Finance** calculators: `compoundInterest`, `simpleInterest`, `emi`,
  `loanRepayment`, `savingsGrowth`, `inflationAdjustedValue`, `futureValue`,
  `presentValue`, `cagr`, `roi`, `ruleOf72`.
- **Tax** calculators: `progressiveTax` (generic marginal-bracket engine),
  `effectiveTaxRate`, `marginalTaxRate`.
- **Percentage** calculators: `percentageChange`, `percentageIncrease`,
  `percentageDecrease`, `percentageOf`, `whatPercentageOf`, `ratio`,
  `splitByRatio`.
- **Utilities**: `ValidationError`, input assertions (`assertNumber`,
  `assertNonNegative`, `assertPositive`, `assertInteger`, `assertInRange`),
  `round`, `periodsPerYear`, `PERIODS_PER_YEAR`, `Frequency` type, and
  `VERSION`.
- Full TypeScript types and JSDoc with examples for every function.
- Dual ESM + CommonJS builds with bundled type declarations via `tsup`.
- Vitest unit-test suite (35 tests) covering all categories.
- Runnable examples for payroll, finance, tax, and percentage modules.
- Professional README with API reference and a **UIF reference section**
  (documented formula, not a bundled function) linking to
  <https://uifcalculator.com>.

[Unreleased]: https://github.com/your-org/salary-finance-toolkit/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/your-org/salary-finance-toolkit/releases/tag/v1.0.0
