# Arbeidstilsynet/action-dotnet-build

Opinionated action for dotnet workflows. Restores, checks formatting, lints, builds, and tests a .NET solution/project.

## Requirements

- The `working-directory` must contain a single .NET solution or project compatible with the specified .NET SDK version.
- [CSharpier](https://csharpier.com) must be installed in the working directory or an ancestor directory (e.g., via `dotnet tool install csharpier --create-manifest-if-needed`).
- From v3 onwards, this action uses [Microsoft Testing Platform v2](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-platform-intro) as the test runner and generates code coverage based on it. For xUnit integration, see [xUnit with Microsoft Testing Platform](https://xunit.net/docs/getting-started/v3/microsoft-testing-platform).

## Inputs

| Name                 | Description                             | Required | Default |
|----------------------|-----------------------------------------|----------|---------|
| working-directory    | The directory to run dotnet commands in | Yes      |         |
| dotnet-version       | The version of dotnet to use            | No       | 10.0.x  |
| enable-sonar         | Enable SonarCube analysis              | No       | false   |
| sonar-token          | SonarCube token                        | No       |         |
| sonar-project-key    | SonarCube project key                  | No       |         |
| sonar-organization   | SonarCube organization                 | No       |         |

## Usage

### Basic Usage

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

### With SonarCube Integration

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
        with:
          fetch-depth: 0 # Shallow clones should be disabled for better analysis relevancy
      - uses: Arbeidstilsynet/action-dotnet-build@v2
        with:
          working-directory: ./src
          enable-sonar: 'true'
          sonar-token: ${{ secrets.SONAR_TOKEN }}
          sonar-project-key: 'your-project-key'
          sonar-organization: 'your-organization'
```

## Versioning

This repository uses a simple versioning system based on the `VERSION` file.
When you update the `VERSION` file and push to `main`, a Git tag with that version is created or updated automatically by the workflow.
If you make breaking changes to the action, bump the version and update `CHANGELOG.md`.
