# Adding text to the beginning of a file

## Problem
You want to quickly add a piece of text to the beginning of a file.

## Solution
The simplest way is to just print the text together with the content of the file to a temporary file, then copy the temporary file to the original file.

```
    echo 'Begin' | cat - <file> > temp && mv temp <file>
```

Another way is to use `sed` program to insert the text to the beginning of the file and use edit in place functionality of `sed` so that we don't have to create temporary file.

```
    sed -i '1s/^/Begin\n/' <file>

    # A shorter version
    sed -i '1iBegin' <file>
```
