# Changelog

All notable changes to claude-ads are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.5.1] - 2026-04-14

### Security

- Added shared SSRF validation module (`scripts/url_utils.py`) used by all URL-handling scripts
- Blocked IPv4 private ranges (127/8, 10/8, 172.16/12, 192.168/16, 169.254/16, 0/8, 100.64/10) and IPv6 (::1, fc00::/7, fe80::/10, ::ffff:0:0/96)
- DNS resolution failures now reject the URL instead of silently passing through
- Added `_sanitize_error()` to strip API keys, tokens, and passwords from error messages
- Added reference image extension allowlist to prevent arbitrary file reads
- Added batch size limit (50 jobs max) and dimension bounds (8192px max)
- Validated Replicate API response URLs are HTTPS before fetching
- Truncated Stability API error responses to prevent info leakage

### Changed

- GitHub Actions pinned to full SHA hashes instead of mutable version tags
- Dependabot auto-merge restricted to patch updates only (was all versions)
- CI workflow scoped to `permissions: contents: read` (least privilege)
- `pip-audit` added to CI for dependency vulnerability scanning
- `install.sh` tries standard pip first, falls back to `--break-system-packages` with warning
- `install.sh` trap variable quoting fixed for safer cleanup
- `.gitignore` now excludes `*.pem`, `*.key`, `*.p12`, `*.pfx`, `credentials.json`, `service-account.json`

## [1.4.0] - 2026-04-01

See CHANGELOG history on upstream repo for earlier versions: https://github.com/AgriciDaniel/claude-ads/blob/main/CHANGELOG.md
