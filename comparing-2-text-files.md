# Comparing 2 text files

## Problem
You want to compare 2 text files side by side.

## Solution
Linux already has a tool to do this called `diff`

```
    diff file1 file2
```

The output will be something like this
```
1c1
< 1
---
> 2

```

where the `<` part is in the first file only and the `>` part is in the second file only.

If you want more visual diff you can use `colordiff`
