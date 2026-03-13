# OpenCI React Native CI

[![GitHub Marketplace](https://img.shields.io/badge/Marketplace-OpenCI%20React%20Native%20CI-green?style=flat-square&logo=github)](https://github.com/marketplace/actions/openci-react-native-ci)

A GitHub Action to **lint, type-check, and test** your React Native (Expo) project in one step.

## Features

- 🟢 **Node.js setup** — configurable version (default: 20)
- 📦 **Multi-package-manager** — supports npm, yarn, and pnpm
- 🔍 **ESLint** — zero-warning enforcement (skippable)
- 🔒 **TypeScript type-check** — `tsc --noEmit`
- 🧪 **Jest tests** — with `--passWithNoTests` (skippable)

## Usage

```yaml
name: CI

on:
  pull_request:
  push:
    branches: [main]

jobs:
  ci:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: open-ci-io/react-native-ci-action@v1
```

### With options

```yaml
- uses: open-ci-io/react-native-ci-action@v1
  with:
    node-version: '18'
    package-manager: 'yarn'
    working-directory: './my-app'
    skip-lint: 'true'
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `node-version` | Node.js version to use | No | `20` |
| `package-manager` | Package manager: `npm`, `yarn`, or `pnpm` | No | `npm` |
| `working-directory` | Working directory for the project | No | `.` |
| `skip-lint` | Skip ESLint step | No | `false` |
| `skip-test` | Skip test step | No | `false` |

## What it does

1. **Setup Node.js** using the specified version
2. **Install dependencies** with the chosen package manager (respecting lockfiles)
3. **Run ESLint** with zero-warning policy (unless skipped)
4. **TypeScript type-check** via `tsc --noEmit`
5. **Run tests** via Jest with `--passWithNoTests` (unless skipped)

## License

MIT — see [LICENSE](./LICENSE) for details.
