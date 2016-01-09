# Splitting and merging files

## Problem
We want to split a big file into smaller files and join them back later to the original file.

## Solution
Use `split` to split file easily

```
    # Default split will create xaa, xab, etc files
    split <FILE>
    > xaa
    > xab
    > xac
    > xad

    # Split with fixed number of files, numeric suffix of 3 digits, and prefix
    split <FILE> -n 10 -a 3 -d <PREFIX>

    # Split with fixed file size, numeric suffix of 3 digits, and prefix
    split <FILE> --bytes=1000 -a 3 -d <PREFIX>
```

To merge splitted files, simply `cat` them together

```
    cat prefix* > <NEWFILENAME>
```
