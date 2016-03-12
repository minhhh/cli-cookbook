# Replacing strings
## Problem
You want to replace one string by another in one or many files.

## Solution
You can use `sed` to do various string manipulation tasks

To replace `old-word` by `new-word`
```
    sed -i 's/old-word/new-word/g' *.txt

    #in mac
    sed 's/old-word/new-word/g' -i '' *.txt
    sed 's/old-word/new-word/g' *.txt
```

Some times the words contain single quotes, in these cases, we have to escape them like so

```
    sed 's/old-word/new'\''word/g' *.txt
```

If you want `sed` to read from standard input, you have to use `-e` option

```
    echo "hello world" | sed -e 's/hello/hi/g'
    > hi world
```
