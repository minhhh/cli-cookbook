# Finding files in a folder

## Problem
You want to find a file by name in a folder, but also want to exclude certain folder in the find path. Also, you want to run some command after finding the files.

## Solution
The `find` tool can find file/folders by name, exclude certain folders/files and execute command on found items.

Find files by name, excluding the git folders
```
    find . -not -path "./.git/*" -iname "my.png"
```

Remove all .svn files in a directory

```
    find . -name ".svn" -exec rm -rf {} \;
```

