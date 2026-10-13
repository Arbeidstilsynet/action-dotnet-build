# Changelog

## v4

- Speed up the pipeline (non-breaking):
  - Run `dotnet format style` and `dotnet format analyzers` concurrently with `--no-restore`
  - Run `dotnet test --no-build` instead of rebuilding before tests
- Add optional SonarQube Cloud steps
- Add optional inputs `skip-csharpier` and `skip-style-analyzers`

## v3

Use Microsoft Testing Platform v2 as test runner and generate cobertura coverage

## v2

Bump default value for `dotnet-version` to `10.0.x`

## v1

Initial release
