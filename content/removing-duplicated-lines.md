# Removing duplicated lines

## Problem
You want to remove duplicated lines in a file or from stdin.

## Solution
You can combine `uniq` and `sort` to achieve this.

```
    sort garbage.txt | uniq -u
    cat garbage.txt | sort | uniq -u
```

