# Execute a command at a specified time

## Problem
You want to run a command at a specified time, or at a certain amount of time from now.

## Solution
Use `at` command to run arbitrary commands and scripts at a specified time.

There are 2 ways to run `at`: from user input or from a script

To run from user input
```
    at <time>
    ...type in the commands
    Ctrl-D
```

To run from a script
```
    at <time> -f <script>
```

To run a command immediately
```
    at now
```

To run a command at a specific time in the future

```
    # run this job at 10:00 Jan 10, 2015
    at 10:00 Jan 10 2015

    # run this job at midnight, noon, or teatime, respectively
    at midnight
    at noon
    at teatime

    # run this job at noon today or tomorrow
    at noon today
    at noon tomorrow
```

To run a command after an amount of time has elapsed from now, just add `+` to the time

```
    # run this job after 3 minutes
    at now + 3 minutes

    # run this job at 4pm 3 days from now
    at 4pm + 3 days
```

To list current jobs, use `atq`
```
    atq
```

To remove a job listed by `atq`, use `atrm`
```
    atrm 10
```

`batch` is similar to `at`, but it only executes command when system load levels permit, i.e., when the load average drops below 1.5.
