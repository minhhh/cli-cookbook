# Finding files based on name

## Problem
You want to find files or folders in a directory by name.

## Solution
Use `find` to find files or folders in a folder by name.

Find all files or folder in the current directory whose name is `password.txt`. 

```
    # This command would match any files whose name consisted of the letters `password.txt', regardless of case, including 'password.txt', 'PASSWORD.TXT', and 'password.TXT'.
    find . -iname password.txt
```

We can use some wildcard patterns to make the searching easier in case we don't know the exact names, or we just want to find all files with similar patterns.

```
    # search all files begin with `pass`
    find . -iname 'pass*'

    # file all files with a certain extension
    find . -iname '*.png'
    find . -iname '*.txt'

    # search all files whose name contains `pass` somewhere
    find . -iname '*pass*'
```

To find only file or folder we have to specify the type like so

```
    # search only files
    find . -type f -iname 'win*'

    # search only folder
    find . -type d -iname 'win*'
```

To exclude specific folders we use the `-not -iname` option

```
    find -name "*.js" -not -iname "hello.js"
```

To exclude specific folders we use the `-not -path` option

```
    find -name "*.js" -not -path "./directory/*"
```

Running commands on the files you find.
```
    find . -name '*.md' -exec echo 'Found {}' ';'
    > Found ./android_cli.md
    > Found ./awk.md
    > Found ./bash.md
    > Found ./curl.md
    > Found ./daemons.md
    > Found ./docker.md
    > ...
```

This is similar to "Running a command for each item in a list" part. You can use `awk` or `xargs` to do more advanced things. For simple operations you can use `find`.
