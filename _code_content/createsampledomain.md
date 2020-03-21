---
name: createsampledomain
---

Setup environment variables on Mac:
```bash
export TEMPORAL_CLI_DOMAIN=samples-domain
```

Setup environment variables on Windows:
```bat
set USER=someusername
set TEMPORAL_CLI_DOMAIN=samples-domain
```

Check if samples-domain exists:
```bash
docker run --rm temporalio/tctl:latest d desc
```

Create samples-domain:
```bash
docker run --rm temporalio/tctl:latest d register --rd 7
```
