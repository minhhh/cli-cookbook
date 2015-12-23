# Doing mathematics

## Problem
We want to do simple mathematics

## Solution
Use `bc` command

```
    echo "5.1 * 2" | bc - l
    > 10.2

    echo "scale=10; 1/2" | bc -l
    > .5000000000
```

