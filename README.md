# Arbeidstilsynet/action-dotnet-build

Opinionated action for dotnet workflows. Restores, checks formatting, lints, builds, and tests a .NET solution/project.

## Requirements

- The `working-directory` must contain a single .NET solution or project compatible with the specified .NET SDK version.
- [CSharpier](https://csharpier.com) must be installed in the working directory or an ancestor directory (e.g., via `dotnet tool install csharpier`).

## Inputs

| Name              | Description                             | Required | Default |
|-------------------|-----------------------------------------|----------|---------|
| working-directory | The directory to run dotnet commands in | Yes      |         |
| dotnet-version    | The version of dotnet to use            | No       | 8.0.x   |

## Usage

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: Arbeidstilsynet/action-dotnet-build@v1
        with:
          working-directory: ./src
          dotnet-version: 8.0.x
```
