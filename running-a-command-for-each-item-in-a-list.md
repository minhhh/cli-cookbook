# Running a command for each item in a list
## Problem
A super common thing you need to do is to do something repetively to a lot of files. For instance, change all the file names. For simple task like just changing the extension, you can do `mv *.png *.jpg`. But what if you want to replace spaces in the file name with `-` or `_`. Or maybe you want to add a hash to the file name. Things are a little bit more complicated.

## Solution

The universal solution to all of these problems is `xargs`. Basically, you can print all of the items that you need to do something with and pass it to `xargs` to process them one by one.

The way to do this is:

```
    ...previous command | xargs -n 1 command
```

The `-n 1` part is to ensure that you process the list one at a time. This only work if the previous command doesn't generate string with newline and spaces. If it does then we have to specify another character as delimiter by xargs, usually the null character `\0`. With the find command we can use option -print0.

Let's try to add an extra extension to all our files in a folder
```
    find . ! -path . -print0 | xargs -n 1 -0 -I {} sh -c 'mv "{}" "{}.extra"'
```

The `find . ! -path . -print0` part find all files and folder, excluding current dir `.`. Then `xargs` take each of the name as `{}`, and execute move command `sh -c 'mv "{}" "{}.extra"'` to them.

Let's see how can we replace all spaces in all filenames in a folder with `-`.

```
    find . ! -path . | awk '{ str=$0; gsub(" ", "-", str); print "mv \""$0"\" \""str"\"" "\0"; }' | xargs -n 3 -0 -I {} sh -c '{}'
```

This time we have to do a little more quoting so that we can deal with filenames with space. Basically we generate a string of the command we want to run using `awk`. Then we pass the whole command string to xargs and run it.

It's worth knowing that we can also do this directly with `awk`

```
    .... previous command | awk '{system("command \""$0"\"")}'
```

So the previous command becomes
```
    find . ! -path . | awk '{ str=$0; gsub(" ", "-", str); system("mv \""$0"\" \""str"\"" "\0"); }'
```

In this case using `awk` is simpler. However when you have to process several parameters/lines at a time, `xargs` proves to be more straight forward.

