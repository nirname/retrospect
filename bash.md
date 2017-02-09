# Bash

## Rename files recursively / Change extensions

```bash
find . -name '*.ru.txt' -exec sh -c 'mv "$0" "${0%.ru.txt}.en.txt"' {} \;
```