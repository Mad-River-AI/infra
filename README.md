# infra

> Hosting, deployment, cron configs, runbooks, and operations scripts for **Mad River AI**.

The unglamorous repo. Where the "make it actually run" work lives. If `osint-framework` is the body and `agent-specs` is the brain, this is the circulatory system and the janitor.

🔗 https://madriverai.com &nbsp;·&nbsp; 🐙 https://github.com/Mad-River-AI

---

## What's in here

```
infra/
├── compose/                 # docker-compose stacks
│   ├── n8n.yaml
│   ├── searxng.yaml
│   ├── music-stream.yaml
│   └── mcp-servers.yaml
├── cron/                    # scheduled jobs
│   ├── madriverai-recon/    # nightly domain recon → wiki vault
│   ├── morning-briefing/    # 7am digest
│   └── osint-watchers/      # per-topic monitors
├── deploy/                  # cloud-init, ansible, terraform (TBD)
├── runbooks/                # operational docs
│   ├── squarespace-to-cloudflare-migration.md
│   ├── hostinger-rebuild.md
│   └── incident-response.md
├── monitoring/              # healthchecks, alerts
└── secrets/                 # .env.example files (NEVER real secrets)
```

## Current live state

| service | host | status | notes |
|---|---|---|---|
| `madriverai.com` DNS | Squarespace | live, parking page | nameservers to be repointed |
| Hostinger VPS (4 vCPU / 16GB / 200GB NVMe) | external | **off** | hosts n8n, searxng, music stream when up |
| github.com/Mad-River-AI | github.com | live | 3 public repos as of 2026-06-12 |
| morning briefing cron | hermes scheduler | scheduled, 7am | first fire 2026-06-13 |
| domain recon cron | hermes scheduler | running | feeds `~/OBSIDIAN/wiki/Mad River AI/00-recon/` |

## Conventions

- **One compose file per service.** Stacks stay composable.
- **Secrets in `.env`, never in compose.** `.env` is `.gitignore`d. `secrets/.env.example` is the template.
- **Cron scripts are idempotent.** They can run twice without breaking.
- **Runbooks assume 3am and a half-asleep operator.** If a step needs nuance, it doesn't belong in a runbook.

## Status

🚧 **Early.** This repo is being built as ops needs arise, not in advance.

## License

MIT. See [LICENSE](LICENSE).

## Contact

- Issues: this repo
- Ops: [@trip7s](https://github.com/trip7s)

---

*Heated in Indiana. Cooled by Cloudflare.*
