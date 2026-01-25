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

Run the default [ENTRYPOINT](https://docs.docker.com/reference/dockerfile/#entrypoint). The `--rm` flag is optional and deletes the container on exit.

```plaintext
; docker run --rm cgr.dev/chainguard/malcontent:latest
NAME:
   malcontent - Detect malicious program behaviors

USAGE:
   mal [GLOBAL FLAGS] <command> [COMMAND FLAGS] <path>
...
```

Use `--mount` to let the container read from a directory. Adjust entrypoint args to use the new path.

```plaintext
; docker run \
   --rm \
   --mount type=bind,source=.,target=/tmp,readonly \
   cgr.dev/chainguard/malcontent:latest \
   -- \
   analyze /tmp/whatever.exe
🔎 Scanning "/tmp/whatever.exe"
...
```
