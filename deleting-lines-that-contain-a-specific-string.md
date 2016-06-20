# Deleting lines that contain a specific string

## Problem
In a lot of occasions, you would want to remove a particular line in a file if it exists.

## Solution
You can use a lot of tools to do this such as `awk`, `bash`, `sed`, etc.

Using `sed` is pretty intuitive. To remove a line contains a specific string we do like this

```
    # Will remove all lines containing helloworld
    sed -i '/helloworld/d' ./infile
```

Sometimes we want to match the whole line, we can do like this

```
    # Will remove all lines which are exactly `helloworld`
    sed -i '/^helloworld$/d' ./infile
```

