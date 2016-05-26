# Batch renaming
## Problem
This is actually one of the most common problems that we encouter everyday. Sometime somewhere someone will name all the files incorrectly and we want to change the extensions or some part of the filename to suit our needs.

## Solution

To change one kind of file name to another, we use `bash` for loop with `find`

```
    # change from .html to .txt
    for file in *.html; do
        mv "$file" "`basename $file .html`.txt"
    done
```

You can probably do the same with `awk` as well. The principle is to list the file first then rename them one by one.

However, there's a more convenient way to batch rename, which is the `rename` command. You can use it like so

```
    rename 's/\.html$/\.txt/' *.html
```

The syntax is `rename "regex-rule" <files>`. So if you can do some simple regex, it's better to do this way.

Another example is to change all filenames to lower case or upper case. Again, you can use `rename`

```
    # uppper to lower
    rename -f 'y/A-Z/a-z/' *

    #  lower to uppper
    rename -f 'y/a-z/A-Z/' *
```

