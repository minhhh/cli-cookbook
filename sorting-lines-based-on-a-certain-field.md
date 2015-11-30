# Sorting lines based on a certain field

## Problem
You want to sort a list of lines from a file or from stdin based on a certain field, provided all the lines follow the same format.

## Solution
First, you can sort the whole line with `sort`. For instance, you can sort lines in `/etc/password`, which will sort by the username since the username is the first field in each line.
```
    # sort password file by username
    sort /etc/passwd
```

However, most of the time we want to sort the file based on a field in the middle, and/or some complex formula of the fields, for instance, the ratio between field 2 and field 3. In such cases, we will use `awk` to calculate the derived field then use `sort` on the final result

```
    # sort based on field 2 / field 1 then print the result at the beginning of the line
    cat somefile.txt | awk '{ratio = $2/$1; print ratio, $0;}' | sort -rnk1 | head
```

Real world example: Counting unique ip access in apache log in a month

```
    grep Jan/2004 access.log | grep foo.php | \
    awk '{ print $1; }' |  sort -n | uniq -c | \
    sort -rn | head
```
