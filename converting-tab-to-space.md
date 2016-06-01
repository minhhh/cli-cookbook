# Converting tab to space

## Problem
You want to convert tab to space and vice versa.

## Solution
To convert from tab to space you can use `expand`

```
    # convert tab to 4 space in all java files
    find . -name '*.java' ! -type d -exec bash -c 'expand -t 4 "$0" > /tmp/e && mv /tmp/e "$0"' {} \;
```

To convert all 4 spaces to tab, use `unexpand`

```
    unexpand -t 4 <input_file>
```
