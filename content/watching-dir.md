# Watching a directory and execute command on file change

## Problem
Watch a file sets or directory and run a command when anything is added, changed or deleted.

## Solution
Use python [watchdog](https://pypi.python.org/pypi/watchdog) module, which has a command line tool called `watchmedo`

```bash
    watchmedo shell-command --recursive --command 'echo ${watch_event_type}' -w -W . \
    | xargs -n 1 -I {} sh -c 'if [ "{}" = "modified" ]; then clear; make unittest; fi'
```

Alternatively, can use nodejs [onchange](https://www.npmjs.com/package/onchange) module

```bash
    onchange 'app/**/*.js' 'test/**/*.js' -- npm test
```
