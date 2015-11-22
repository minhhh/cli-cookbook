# Printing a file

## Problem
We want to print a file with different representation. We also want to print various information related to the file.

## Solution
For text file we can use various command like `cat`, `head`, `tail`, `more`, `less`

If we want to see file in hex format we can use `hexdump`

```
    hexdump <file>
```

To print information about the file such as file type we can use `file` command

```
    file <file>
```

To count the number of characters or lines, we use `wc`

```
    # this shows number of line, words, character respectively
    wc <file>

    # show number of lines
    wc -l <file>

    # show number of words
    wc -w <file>

    # show number of characters
    wc -c <file>
```
