# Merge content of 2 files side by side

## Problem
You want to show the content of 2 files next to each other, line by line. For instance, one file contains id and the other contains names.

## Solution
You can use `paste` to achieve this.

Suppose `file1` contains names
```
Mark Smith
Bobby Brown
Sue Miller
Jenny Igotit
```
and `file2` contains numbers

```
555-1234
555-9876
555-6743
867-5309
```

You can use `paste` like so
```
    # Merge with default separator: tab
    paste file1 file2
    > Mark Smith	555-1234
    > Bobby Brown	555-9876
    > Sue Miller	555-6743
    > Jenny Igotit	867-5309

    # merge with delimiter comma (,)
    paste -d, file1 file2
    > Mark Smith,555-1234
    > Bobby Brown,555-9876
    > Sue Miller,555-6743
    > Jenny Igotit,867-5309
```

