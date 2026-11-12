# moabb-mirror

A moabb mirror for bci datasets.

## usage

Download github release and untar at `~/mne_data`. this is the default location that moabb benchmark will read. 

you may use this to extract all into your home directory to make `moabb` read it:

```bash
#!/bin/bash
set -e

SRC="home/runner/mne_data"
DEST="$HOME/mne_data"

mkdir -p "$DEST"

# Group split archives by base name (a, b, ...)
for base in $(ls "$SRC"/*.tar.* | sed -E 's/.*\/([^/]+)\.tar\.[0-9]+$/\1/' | sort -u); do
    echo "Extracting $base.tar.* ..."
    cat "$SRC/$base".tar.[0-9][0-9][0-9] | tar -xf - -C "$DEST"
done

echo "Done. Extracted into $DEST"
```
