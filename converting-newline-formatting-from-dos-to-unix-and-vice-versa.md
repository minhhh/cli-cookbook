# Converting newline formatting from DOS to Unix and vice versa

## Problem
You have some files that use Windows newline characters but you want to use them in Linux or MacOS, or vice versa.

## Solution
You can use a lot of tools to do this such as `sed, `perl`, `dos2unix`, `unix2dos`

One simple way is to use `perl` so you don't have to install new programs

```
    perl -pi -e 's/\r\n|\n|\r/\r\n/g' file-to-convert  # Convert to DOS
    perl -pi -e 's/\r\n|\n|\r/\n/g'   file-to-convert  # Convert to UNIX
```

If we want to batch convert files, we can combine it with `find` and `xargs`

```
    # Find all .cs file and convert newline to UNIX
    find . -iname *.cs -print0 | xargs -n 1 -I {} -0 perl -pi -e 's/\r\n|\n|\r/\n/g' '{}'
```


**References**

* https://stackoverflow.com/questions/6373888/converting-newline-formatting-from-mac-to-windows
