# Finding files based on size

## Problem
You want to find the largest file or folders, maybe recursively. You also want to find files that are bigger/smaller than X bytes

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

To find files smaller/larger than X bytes we will also use `find` command with the `-size` option

```
    // find files larger than 4096 bytes
    find . -type f -size +4096c

    // find files smaller than 1M
    find . -type f -size -1M
```

Options for the `-size` switch
```
    -size n[ckMGTP]
        True if the file's size, rounded up, in 512-byte blocks is n.  If n is followed by a c, then the primary is true if the
        file's size is n bytes (characters).  Similarly if n is followed by a scale indicator then the file's size is compared to n
        scaled as:

        k       kilobytes (1024 bytes)
        M       megabytes (1024 kilobytes)
        G       gigabytes (1024 megabytes)
        T       terabytes (1024 gigabytes)
        P       petabytes (1024 terabytes)
```
