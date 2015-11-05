# Listing file and folder sizes

## Problem
You want to print the sizes of all files and folders in the current folder from largest to smallest

## Solution
We simply run `du` command on each file and folder in the current folder then sort them using `sort`

```
    ls -A | awk '{system("du -sm \""$0"\"")}'| sort -nr | head
```

To list only folders

```
    ls -Al \
    | egrep '^d' \
    | awk '{printf $9; for (x=10; x <= NF; x  ) {printf " "$x;}; print ""}' \
    | awk '{system("du -sh \""$0"\"")}'
```

To list only files
```
    ls -Al | egrep -v '^d' \
    | awk '{printf $9; for (x=10; x <= NF; x  ){printf " "$x;}; print ""}' \
    | awk '{system("du -sh \""$0"\"")}'
```

## References
* [http://groups.google.com/group/comp.unix.shell/browse_thread/thread/aebcbd0591714584/5e496ed7cfbe6eb1](http://groups.google.com/group/comp.unix.shell/browse_thread/thread/aebcbd0591714584/5e496ed7cfbe6eb1)
* [http://en.wikipedia.org/wiki/Xargs](http://en.wikipedia.org/wiki/Xargs)
* [http://www.cyberciti.biz/faq/linux-list-just-directories-or-directory-names/](http://www.cyberciti.biz/faq/linux-list-just-directories-or-directory-names/)
