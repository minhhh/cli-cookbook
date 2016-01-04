# Joining all lines in a file

## Problem
You want to join all lines in a file, often separated by a comma

## Solution
You can use `paste` to achieve this like so

```
    # Join with tab separate each line
    paste -s <filename>

    # join with delimiter comma
    paste -d, -s <filename>
```
