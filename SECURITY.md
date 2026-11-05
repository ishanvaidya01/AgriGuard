# Security Policy

## Supported versions

AgriGuard does not publish versioned releases. Security fixes are applied to the
latest commit on `main`.

| Version | Supported |
|---|---|
| Latest `main` | Yes |
| Older commits, forks, and modified deployments | No |

## Reporting a vulnerability

Please report security issues privately. Do **not** open a public issue.

- Email: [ishan.vaidya01@gmail.com](mailto:ishan.vaidya01@gmail.com)
- GitHub Security Advisories: [open a private advisory](https://github.com/ishanvaidya01/AgriGuard/security/advisories/new)

Include the affected endpoint or file, reproduction steps, and the impact you
believe the issue has. Do not attach real personal data or a malicious model
file directly; describe it and arrange a safe transfer if needed.

## Scope

Examples of in-scope reports:

- Path traversal or arbitrary file write through the upload filename
- Unbounded uploads or resource exhaustion in the prediction endpoint
- Unsafe deserialization or code execution when loading a model checkpoint
- Cross-site scripting in pages that render model output or user input
- Overly permissive CORS that enables a concrete attack
- Exposed credentials, datasets, or private user images

Out of scope:

- The inherent accuracy limits of a 15-class PlantVillage model
- Incorrect agricultural advice in the demo remedy text
- Vulnerabilities in third-party sites reached through outbound links
- Missing security headers on a local development server
- Reports that require a compromised browser, host, or network

## Known prototype constraints

- The backend allows all origins (`allow_origins=["*"]`). Restrict this before
  exposing a production deployment.
- The frontend enforces a 10 MB limit, but the server does not independently
  enforce a request-size limit.
- Uploaded files are written to a temporary path under `backend/model/` using
  the submitted filename. Treat this code as a prototype, not a hardened
  multi-tenant service.
- Model checkpoints are loaded with `tf.keras.models.load_model`. Only load
  weights from a source you trust.
- There is no authentication or authorization. The login and registration
  screens are client-side demonstrations and do not protect any route.

## Response expectations

Reports are reviewed on a best-effort basis by the maintainer. No fixed response
or remediation deadline is promised. Please allow time for a fix before public
disclosure, and coordinate disclosure through the private advisory.

## Deployment guidance

- Serve the API over HTTPS and replace the wildcard CORS policy with an explicit
  allowlist of frontend origins.
- Add request-size, rate, and concurrency limits at the reverse proxy or
  application layer.
- Store and load model files from a controlled location with integrity checks.
- Keep TensorFlow, FastAPI, and their transitive dependencies patched.
- Do not enable debug mode or expose stack traces to end users.
