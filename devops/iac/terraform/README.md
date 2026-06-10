# Terraform

Terraform modules and environment configurations.

## Structure (planned)

```
terraform/
├── modules/
│   ├── app-service/
│   ├── sql-database/
│   └── key-vault/
├── environments/
│   ├── dev/
│   ├── staging/
│   └── production/
└── backend.tf         # Remote state configuration
```

## Conventions

- One state file per environment.
- Use `terraform plan` in CI before `apply`.
- Pin provider versions in `versions.tf`.
- Never commit `.tfstate` files or secrets.
