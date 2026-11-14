---
name: hermes-delegation
description: Delegate smart home (Home Assistant), Telegram notifications, Proxmox, and remote homelab tasks to the Hermes Agent running on hermes-ct.
version: 1.0.0
---

# Hermes Agent Delegation

Delegate smart home automation, Home Assistant device control, Telegram notifications, and container tasks to the autonomous Hermes Agent running on `hermes-ct` (192.168.1.125).

## Methods of Delegation

### Method 1: Hermes OpenAI-Compatible API (Fast & Programmatic)
Hermes exposes an API server on port `8642`. You can query it with curl or python:

```bash
curl -s -X POST http://192.168.1.125:8642/v1/chat/completions \
  -H "Authorization: Bearer a8bf90ac8a189a5a4cff711c887cd4223d6cb9494baa91b07f046fd2b2d8bbb6" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "hermes-agent",
    "messages": [{"role": "user", "content": "TAREA_A_DELEGAR"}]
  }'
```

### Method 2: Direct CLI via SSH
Execute a direct command in Hermes context via SSH:

```bash
ssh hermes-ct "hermes chat -q 'TAREA_A_DELEGAR'"
```

### Method 3: Via Herdr
If controlling workspaces in Herdr:
```bash
herdr --machine fa93e06d3d6b584abf5f9c791abe501a agent list
```
