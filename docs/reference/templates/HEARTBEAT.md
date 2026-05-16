---
summary: "Workspace template for HEARTBEAT.md"
title: "HEARTBEAT.md template"
read_when:
  - Bootstrapping a workspace manually
---

```markdown
# HEARTBEAT.md - Periodic Check Checklist

## High Priority (every heartbeat)
- [ ] System health: openclaw status normal?
- [ ] Gateway: systemctl --user is-active openclaw-gateway

## Medium Priority (every 1-2 hours)
- [ ] Disk space: df -h / (alert at 80%)
- [ ] Memory: free -h (alert at 90%)
- [ ] Config backup: openclaw.json.last-good up to date?

## Low Priority (every 12-24 hours)
- [ ] Security audit: openclaw security audit
- [ ] Update check: openclaw update status
- [ ] Error log check: journalctl --user -u openclaw-gateway -n 50 | grep -i error
- [ ] Skills audit: MEMORY.md needs update?

## Alert Thresholds
- CPU > 80% for 5min → warning
- Disk < 10GB → critical
- Gateway restarts > 1/day → investigate
- Session files > 5MB → compress

## Auto-discovery
Check for community plugins: python3 ~/.openclaw/plugin-skills/plugin-marketplace/scripts/marketplace.py sync &>/dev/null
```

## Related

- [Heartbeat config](/gateway/config-agents)
