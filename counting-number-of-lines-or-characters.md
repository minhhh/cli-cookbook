# Counting number of lines or characters

## Problem
We want to count the number of lines, characters or words in a file

## Solution
To count the number of characters, words or lines, we use `wc`

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

To make a list of word frequency in a document, we can combine `wc`, `sort` and `awk` like so

```
    cat ~/bitbucket/wiki/about.md | tr ' ' '
    ' | sort | uniq -c | sort -rnk1

    # result
    51 to
    39 and
    36 I
    31 of
    31 a
    30 the
    ...
```
