# Counting the number of files or folders
## Problem
You want to count the number of files and/or folders in a certain folder

## Solution
The simplest solution is to combine `find` and `wc`

To count all files and folders recursively

```
    # Count all files and folders in the current folder
    find . | wc -l
    > 5254

    # Count all files and folders in a certain folder with name <name>
    find <name> | wc -l
    > 5054
```

To count only files

```
    find . -type f | wc -l
    > 4232
```

To count only folders (this will also count the current folder so remember to subtract 1 if you want the correct number)

```
    find . -type d | wc -l
    > 432
```

To count folders and files in the current folder only, not recursively, use `-depth 1` parameter

```
    find . -type d -depth 1 | wc -l
    > 29

    find . -type f -depth 1 | wc -l
    > 2
```
