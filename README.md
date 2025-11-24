# Arbeidstilsynet/action-dotnet-build

Opinionated action for dotnet workflows. Restores, checks formatting, lints, builds, and tests a .NET solution/project.

## Requirements

- The `working-directory` must contain a single .NET solution or project compatible with the specified .NET SDK version.
- [CSharpier](https://csharpier.com) must be installed in the working directory or an ancestor directory (e.g., via `dotnet tool install csharpier --create-manifest-if-needed`).
- From v3 onwards, this action uses [Microsoft Testing Platform v2](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-platform-intro) as the test runner and generates code coverage based on it. For xUnit integration, see [xUnit with Microsoft Testing Platform](https://xunit.net/docs/getting-started/v3/microsoft-testing-platform).

## Inputs

| Name              | Description                             | Required | Default |
|-------------------|-----------------------------------------|----------|---------|
| working-directory | The directory to run dotnet commands in | Yes      |         |
| dotnet-version    | The version of dotnet to use            | No       | 10.0.x  |

## Usage

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
      - uses: Arbeidstilsynet/action-dotnet-build@v2
        with:
          working-directory: ./src
```

## Versioning

This repository uses a simple versioning system based on the `VERSION` file.
When you update the `VERSION` file and push to `main`, a Git tag with that version is created or updated automatically by the workflow.
If you make breaking changes to the action, bump the version and update `CHANGELOG.md`.
