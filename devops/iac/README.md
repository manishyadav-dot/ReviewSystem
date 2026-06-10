# Infrastructure as Code

Reproducible infrastructure provisioning templates.

## Platforms

| Directory | Tool | Target |
|-----------|------|--------|
| `terraform/` | Terraform | Cloud-agnostic or multi-cloud |
| `bicep/` | Azure Bicep | Azure-native resources |

## Managed Resources (planned)

- App Service or Container Apps (frontend + backend hosting)
- Azure SQL Database or SQL Server on VM
- Key Vault (secrets management)
- Application Insights (monitoring and logging)
- Virtual Network and security groups

## Conventions

- Separate state per environment.
- Use modules for reusable resource patterns.
- Document all variables in module README files.
