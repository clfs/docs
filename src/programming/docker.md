# Docker

## Delete

Remove unused stuff. Add the `--all` flag to remove unused images too.

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

## Export

Export a tarball without running the image.

```plaintext
; docker save atdr.meo.ws/archiveteam/warrior-dockerfile > out.tar
```

Explore the tarball with [`dive`](https://github.com/wagoodman/dive) (`brew install dive`).

- Zoom out to see everything well.
- Switch between the left and right panes with <kbd>Tab</kbd>.
- Rotate through left-pane sections with <kbd>←</kbd> and <kbd>→</kbd>.
- The <kbd>Ctrl</kbd> <kbd>e</kbd> "Extract File" shortcut doesn't work ([Issue#620](https://github.com/wagoodman/dive/issues/620)).

```plaintext
; dive --source docker-archive out.tar
```

## Run

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
