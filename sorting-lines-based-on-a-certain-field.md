# Sorting lines based on a certain field

## Problem
You want to sort a list of lines from a file or from stdin based on a certain field, provided all the lines follow the same format.

## Solution
First, you can sort the whole line with `sort`.

For instance, you can sort lines in `/etc/password`, which will sort by the username since the username is the first field in each line.

```
    # sort password file by username
    sort /etc/passwd

    # original content
    _kadmin_changepw:*:219:-2:Kerberos Change Password Service:/var/empty:/usr/bin/false
    _devicemgr:*:220:220:Device Management Server:/var/empty:/usr/bin/false
    _webauthserver:*:221:221:Web Auth Server:/var/empty:/usr/bin/false
    _netbios:*:222:222:NetBIOS:/var/empty:/usr/bin/false
    _warmd:*:224:224:Warm Daemon:/var/empty:/usr/bin/false
    _dovenull:*:227:227:Dovecot Authentication:/var/empty:/usr/bin/false

    # content after sorting
    _devicemgr:*:220:220:Device Management Server:/var/empty:/usr/bin/false
    _dovenull:*:227:227:Dovecot Authentication:/var/empty:/usr/bin/false
    _kadmin_changepw:*:219:-2:Kerberos Change Password Service:/var/empty:/usr/bin/false
    _netbios:*:222:222:NetBIOS:/var/empty:/usr/bin/false
    _warmd:*:224:224:Warm Daemon:/var/empty:/usr/bin/false
    _webauthserver:*:221:221:Web Auth Server:/var/empty:/usr/bin/false
```

However, most of the time we want to sort the file based on a field in the middle. In this case we use sort by `field` feature.

```
    # Sort by the second field
    cat somefile.txt | sort -rnk2

    # original content
    x   1   2
    x   2   2
    x   3   2
    x   12   2
    x   9   2
    x   3   2

    # content after sorting
    x   12   2
    x   9   2
    x   3   2
    x   3   2
    x   2   2
    x   1   2
```

In a more general case, we want to sort by calculating a value based on some fields, for instance, the ratio between field 2 and field 3. In such cases, we will use `awk` to calculate the derived field then use `sort` on the final result

```
    # sort based on field 3 / field 2 then print the result at the beginning of the line
    cat somefile.txt | awk '{ratio = $2/$1; print ratio, $0;}' | sort -rnk1

    # original content
    x   1   2
    x   2   2
    x   3   2
    x   12   2
    x   9   2
    x   3   2

    # content with the calculated value inserted as the first field: cat somefile.txt | awk '{ratio = $2/$1; print ratio, $0;}'
    2 x   1   2
    1 x   2   2
    0.666667 x   3   2
    0.166667 x   12   2
    0.222222 x   9   2
    0.666667 x   3   2

    # content after sorting
    2 x   1   2
    1 x   2   2
    0.666667 x   3   2
    0.666667 x   3   2
    0.222222 x   9   2
    0.166667 x   12   2
```

Real world example: Counting unique ip access in apache log in a month

```
    grep Jan/2004 access.log | grep foo.php | \
    awk '{ print $1; }' |  sort -n | uniq -c | \
    sort -rn | head
```
