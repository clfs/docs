# Docker

Remove unused stuff.

```plaintext
; docker system prune
WARNING! This will remove:
  - all stopped containers
  - all networks not used by at least one container
  - all dangling images
  - unused build cache

Are you sure you want to continue? [y/N] y
...
```

Run the default [ENTRYPOINT](https://docs.docker.com/reference/dockerfile/#entrypoint).

```plaintext
; docker run cgr.dev/chainguard/malcontent:latest
NAME:
   malcontent - Detect malicious program behaviors

USAGE:
   mal [GLOBAL FLAGS] <command> [COMMAND FLAGS] <path>
...
```

Let the container read from the current directory.

```plaintext
; docker run \
    --mount type=bind,source=.,target=/tmp,readonly \
    cgr.dev/chainguard/malcontent:latest \
    -- \
    analyze /tmp/whatever.exe
🔎 Scanning "/tmp/whatever.exe"
...
```
