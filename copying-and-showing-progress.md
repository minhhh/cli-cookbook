# Copying and showing progress

## Problem
You constantly copying big folders or big files. You see the files are being copied, but it's quite annoying when copying big files that you don't know how much of the file has been copied.

## Solution

You can use `rsync` with `-P` options

```
    rsync -larP source dest
    > t/a
    >         19 100%    0.04kB/s    0:00:00 (xfer#843, to-check=8/1137)
    > t/b
    >         35 100%    0.08kB/s    0:00:00 (xfer#844, to-check=7/1137)
    > ...
```

What's even better about `rsync` is that it won't copy files that are the same in the destination so the next time you change something in the source folder you can execute the same command again and it will only copy the change, not the whole folder again.

Still, when copying a folder with a lot of files, you still don't know the copying progress. In this case, we can pipe the result of `rsync` to another program called `pv`. This `pv` program will show you a progress bar and ETA time.

```
    export SOURCE=<source> DEST=<dest> && export SC=$(find "$SOURCE" | wc -l) && rsync -vrltd  --stats --human-readable "$SOURCE" "$DEST" | pv -lep -s $SC > /dev/null
```

Even though this looks complicated, it's actually quite straight forward. First we use temporary variables to store the source and the destination folders. Then we count how many items are there in the source folder. Then we use `rsync` to copy files one by one and print them out. `pv` will pick up the number of lines and use that with the total number of items to calculate the complete percentage.

Note that if you want to copy a folder inside another folder then you should not include `/` in `<source>`, for instance, set it to `MyFolder`. If you want to copy and rename `MyFolder` to `AnotherFolder` then `<source>` should be set to `MyFolder/`.
