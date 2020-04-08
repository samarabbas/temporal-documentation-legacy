---
name: createsamplenamespace
---

Setup environment variables on Mac:
```bash
export TEMPORAL_CLI_NAMESPACE=samples-namespace
```

Setup environment variables on Windows:
```bat
set USER=someusername
set TEMPORAL_CLI_NAMESPACE=samples-namespace
```

Check if samples-namespace exists:
```bash
docker run --rm temporalio/tctl:0.21.1 n desc
```

Create samples-namespace:
```bash
docker run --rm temporalio/tctl:0.21.1 n register --rd 7
```
