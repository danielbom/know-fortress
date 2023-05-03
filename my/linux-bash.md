---
tags: linux, bash
---

```bash
# Find and modify
find -maxdepth 3 -type d -path “*node_modules” | xargs rm -rv
find -maxdepth 3 -type d -path “*node_modules” | xargs -I % rm -rv “%”

# Compress folders
for path in */; do tar -czvf "${path%/}.tar.gz" "$path"; done

# Check disk usage of directories
du --max-depth 3 | sort -n -r | head -n 10
ncdu
tree

# 10 most common words
tr -c ‘[:alnum:]’ ‘[\n*]’ < $1 | stort | uniq -c | sort -nr | head -n 10
tr -c ‘[:alnum:]’ ‘[\n*]’ < $1 | tr ‘[:upper:]’ ‘[:lower:]’
  | fgrep -v -w -f /usr/share/groff/current/eign
  | sort | uniq -c | sort -nr | head-n 11

# Join words
function join_by { local IFS=”$1”; shift; echo “$*”; }
join_by “ “ “Hello” “World!”
```
