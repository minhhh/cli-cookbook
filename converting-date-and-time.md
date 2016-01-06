# Converting date and time

## Problem
We want to quickly convert standard date time format to POSIX time and vice versa.

## Solution
The standard `date` can do this easily

Convert from date to POSIX

```
    date -d "17 June 2015 15:00:00" +%s
    > 1434520800

    # get current date in POSIX
    date +%s
```

Convert from POSIX to date
```
    date -d @1232144092
    > Sat Jan 17 07:14:52 JST 2009
```

By the way to set the current date
```
    date --set "25 July 2014 15:00:00"
```

