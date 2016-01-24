# Generating random file with particular size

## Problem
You want to generate a random file used for testing with a particular size.

## Solution
You can use `dd` to generate file with random content like this

```
    dd if=/dev/urandom of=myFile.dat bs=64M count=16
```
