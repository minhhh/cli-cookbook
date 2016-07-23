# Comparing file names in 2 directories

## Problem
You want to compare the content of 2 directory by filenames, assuming files with the same name will have the same content

## Solution
You can use `diff` like so

```
    diff -rqu <directory-1> <directory-2>
    # Only in directory-1: file1
    # Only in directory-1: file2
    # Only in directory-2: file3
    # Only in directory-2: file4
```


