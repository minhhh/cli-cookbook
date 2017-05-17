# Printing a range of lines

## Problem
You want to print a range of lines from a file or from stdin, not the whole thing. For instance, you may want to print only the first 3 lines, or the last 5 lines, or everything except the first line, or everything except the last 2 lines.

## Solution
First, we can count the number of lines in a file like this

```
    wc -l <file>
    cat <file> | wc -l
```

Print the first `n` line with `head`

```
    head -n 10 <file>
```

Print last `n` line with `tail`

```
    tail -n 10 <file>
```

Print everything except the first `n` line with `tail`

```
    tail -n +7 <file>
```

Print everything except the last `n` line with `head`

```
    head -n -2 <file>
```

Print from line `x` to line `y` with `sed`

```
    sed -n "1,3p" <file>
```
