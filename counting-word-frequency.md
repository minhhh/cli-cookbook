# Counting number of lines or characters
## Problem
We want to count word frequency and sort it from top to bottom.

## Solution

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
