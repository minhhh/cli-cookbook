# Comparing 2 folders

## Problem
You want to compare the content of 2 folders recursively.

## Solution
You can use `diff` with `-rq` option

```
    diff -rq <folder1> <folder2>
```

If you want more detailed report of the differences, you can use a `Nodejs` tool called `dir-compare`. First, install nodejs, then install `dir-compare` by this command `npm install dir-compare -g`. Then you can use it like this:

```
    # Compare files by content
    dircompare -ca <folder1> <folder2>

    # Ignore some folders
    dircompare -d <folder1> <folder2> -x <folder-to-ignore>
```

There are other options such as to exclude directories or files by name. You can discover more by using `dircompare -h`

If you only want to compare folders by filename, not file content, you can use `diff`

```
    diff <(ls -1a ./dir1) <(ls -1a ./dir2)
```
