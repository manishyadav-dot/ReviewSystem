# Azure Bicep

Azure-native infrastructure templates.

## Structure (planned)

```
bicep/
├── main.bicep              # Root deployment template
├── modules/
│   ├── app-service.bicep
│   ├── sql-server.bicep
│   └── key-vault.bicep
└── parameters/
    ├── dev.bicepparam
    ├── staging.bicepparam
    └── production.bicepparam
```

## Conventions

- Use Bicep modules for reusable Azure resource patterns.
- Parameter files per environment — no secrets in parameter files.
- Validate with `az bicep build` in CI before deployment.
