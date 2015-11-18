# Searching text from files

## Problem
You want to search for text in a lot of files swiftly.

## Solution
You can use `grep` or `egrep`

```
    #list only file name
    find . | xargs grep 'string' -sl
    find / -type f -print0 | xargs -0 grep -l "test"

    # print text and file name
    grep -r "redeem reward" /home/tom

    # egrep with regular expression
    egrep "^\s+\"" file1

    # grep excluding files
    grep -ircl --exclude=*.{png,jpg} "foo=" *
    grep -Ir --exclude="*\.svn*" "pattern" *
```

However the much better solution is to use `ag` or `ack`

```
    ag -Q --smart-case --ignore=pack*.js --ignore=Code/tag \
    --ignore-dir=build --ignore-dir=Code/JSON --ignore-dir=Tools --js "test"

    ack -Q --smart-case "test" --js --ignore-file=match:/packed.*\.js/ \
    --ignore-file=is:Code/tag --ignore-dir=build --js "test"
```

