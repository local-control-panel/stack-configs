# stack-configs

Community-maintained configuration templates for WordPress Docker stacks.  
Used by X to deploy and update server configs without requiring an app release.

## Structure

```
stack-configs/
├── manifest.json                  # Version + compatibility info
├── caddy/
│   ├── security.Caddyfile         # Security rules (xmlrpc, uploads, exploit paths)
│   └── rate-limit.Caddyfile       # Rate limiting per endpoint
└── cloudflare/
    └── firewall-presets.json      # Firewall rule presets for Cloudflare WAF
```

## How it works

The control panel fetches `manifest.json` at deploy time and pulls the relevant config files. Configs are cached locally for offline use. A "Check for updates" button in the UI lets you pull the latest version without updating the app itself.

## Versioning

`manifest.json` includes a `minAppVersion` field. When a config change requires a newer app version, bump `minAppVersion` accordingly so older app versions are not served incompatible configs.

## Contributing

PRs welcome — new Cloudflare presets, Caddyfile rules, or improvements to existing ones. Keep each preset self-contained and include a clear `description` field so users know what they're enabling.
