# server-heartbeat

Dead-man switch for the nc-ph-3285 server (incident 2026-10-25). The server sets the repo
variable `HEARTBEAT` every 5 min (`/root/security-audit/bin/heartbeat.sh`, systemd timer
`heartbeat.timer`). `.github/workflows/deadman.yml` runs every 5 min on GitHub, outside the
server; when the heartbeat is older than 15 min it opens an issue assigned to the owner, so
GitHub emails them even if the server is hung. No secrets in this repo.
