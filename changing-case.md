# Changing cases
## Problem
You want to convert lower case to upper case and vice versa

## Solution
You can use multiple tools to do this task. One simple solution is the `tr` program

```
    # convert upper to lower case
    echo "HELLO" | tr '[:upper:]' '[:lower:]'
    > hello

    # convert lower case to upper case
    echo "hello" | tr '[:lower:]' '[:upper:]'
    > HELLO
```

