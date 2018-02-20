# Bash

## Rename files recursively / Change extensions

```bash
find . -name '*ru.yml' -exec sh -c 'mv "$0" "${0%ru.yml}en.yml"' {} \;
```

## Replace string in all files

Ubuntu

```bash
find . -type f -iname "*en.yml" -exec sed -i 's/ru:/en:/g' {} +
```

Mac

```bash
find . -type f -iname "*en.yml" -exec sed -i '' -e 's/ru:/en:/g' {} +
```

## Redirect stderr to pipe

```bash
command 2>&1 >/dev/null
```