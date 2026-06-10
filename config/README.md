# Configuration

Shared configuration references and templates for all environments.

## Contents (planned)

- `appsettings.template.json` — Backend configuration template (no secrets)
- `.env.example` — Frontend environment variable template
- `nuget.config` — NuGet package source configuration
- `.editorconfig` — Cross-IDE code style settings
- `Directory.Build.props` — Shared MSBuild properties for .NET 10 projects

## Conventions

- Templates use placeholder values — real values are injected at deploy time.
- Add `.env`, `appsettings.*.json` (with secrets), and local overrides to `.gitignore`.
- Document all configuration keys in `docs/onboarding/`.
