# Infrastructure Services

External service integrations and adapters.

## Examples (planned)

- `EmailService` — Transactional email via SMTP or provider API
- `FileStorageService` — Blob/file upload and retrieval
- `DateTimeService` — Testable system clock abstraction
- `CurrentUserService` — Resolve authenticated user from HTTP context

## Conventions

- Wrap third-party SDKs behind Application-layer interfaces.
- Handle retries and timeouts for external calls.
- Log all external service failures with correlation IDs.
