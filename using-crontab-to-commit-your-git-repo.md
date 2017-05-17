# Using crontab to commit your git repo

## Problem
You have a private repo that you constantly commit to. The repo is quite trivial so you don't really care about comment convention or other practices, you just want it to be updated. It's quite tedious to commit by hand.

## Solution
Fortunately, we can use `cron` to automate the commit process. First, open your `crontab` like so:

```
crontab -e
```

This will open your crontab with the default editor. There might be some existing lines. What you have to do is to add a line to make auto commit to your repo, then save the text. The line you will add is:

```
*/5 * * * * (cd <path_to_your_repo> && (git add -u && git commit -m "update") || echo "" && git pull --rebase && git push)
```

Replace `<path_to_your_repo> with the correct path to your repo. This command will make a commit with the comment "update" every 5 minutes. You can increase the commit frequency but I think 5 minutes is a good amount. You can check your current `crontab` with `crontab -l`
