# Finding files based on size

## Problem
You want to find the largest file or folders, maybe recursively.

## Solution
Find the largest file/folder non-recursively OR sort files and folders by size
```
    ls -A | awk '{system("du -sh \""$0"\"")}'| sort -hr | head
```

Find the largest file in a folder and all subfolders recursively
```
    find . -type f -print0 | xargs -0 -n 1 du -sh | sort -hr | head

    # display in block of 1024-byte
    find . -type f -print0 | xargs -0 -n 1 du -sk | sort -nr | head
```

This command use `find` to search for all file recursively. The option `-print0` removes the need for `sed` to escape spaces since all fields now are separated by null character. `args -0` makes sure we use null separator.


