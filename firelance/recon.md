---
description: Tools and scripts for information gathering.
---

# Recon

### amass

Scan for domain names for all targets within `targets.json`. Automatically optimizes the performance and uses thousands of DNS resolvers refreshed daily.

```shell
./recon/amass/amass-enum.sh -t -o $OUTPUT_DIR
```

### httprobe

Probe for HTTP servers given a list of domain names.

```shell
./recon/httprobe/httprobe-scan.sh -t -f $INPUT_FILE -o $OUTPUT_DIR
```

