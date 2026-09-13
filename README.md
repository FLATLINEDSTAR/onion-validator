# onion-validator

## Project Purpose
The **onion-validator** repository implements validation logic that checks raw observations from upstream components (crawler, fingerprint, extractor, etc.) for correctness, completeness, and security policy compliance before they are stored or processed further.

## Current Status
**Planning** – only a placeholder README existed. No code has been added yet.

## Why It Exists
Separating validation from data collection enables a clean pipeline where each stage can focus on its core responsibility. Validators can be updated independently without impacting crawlers or the intelligence engine.

## Architecture Role
- **Library** – imported by `onion-crawler`, `tech-fingerprint`, `entity-extractor`, `change-detector`, and ultimately by `onion-intelligence` via the SDK.
- Provides functions such as `ValidateObservation(obs OnionObservation) error` and `SanitizeHeaders(headers map[string]string) map[string]string`.

## Planned Features (MVP)
1. Schema validation for `OnionObservation` (required fields, data types).
2. Security‑policy checks (e.g., disallowing known vulnerable TLS ciphers, leaking IPs).
3. Normalisation helpers (canonical URL, timestamp formatting).
4. Configurable rule sets via a YAML file.

## Installation / Usage (placeholder)
```bash
# Go (primary)
go get github.com/FLATLINEDSTAR/onion-validator
```
*The package will be published after the MVP is complete.*

## Development
- Language: **Go**.
- Follow contribution standards in the organization `.github` folder.

## Testing
- Unit tests for each validator function using table‑driven test cases.
- Fuzz tests for the sanitisation utilities.

## Contributing
Refer to the organization‑wide `CONTRIBUTING.md`.

## Roadmap
- **Phase 1** – Define validation interfaces in `onion-sdk` and implement core validators.
- **Phase 2** – Add configurable rule engine and integration tests with upstream components.
- **Phase 3** – Publish the package and add CI checks.

## Relationship to FLATLINEDSTAR Ecosystem
Validators are a critical middleware that ensures data quality before it reaches the intelligence engine (`onion-intelligence`).

## License
MIT – see LICENSE in the repository root.