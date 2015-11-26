# Shutting down

## Problem
You want to shutdown system, sometimes immediately, sometimes at a certain time or after a certain duration.

## Solution
Use the `shutdown` command with `root` privilege.

To immediately shut down and halt the system
```
    sudo shutdown -h now
```

To immediately reboot the system
```
    sudo shutdown -r now
```

You can optionally send a warning message to all user with `-c` option
```
    sudo shutdown -h now "The system is being shut down now!"
```

To shut down the system at a certain time

```
    # At 4.23 AM
    sudo shutdown -h 4:23

    # At 8.00 PM
    sudo shutdown -h 20:00
```

To shut down and halt the system after a period of time

```
    # In 5 minutes
    sudo shutdown -h +5
```

To cancel a shutdown
```
    sudo shutdown -c
```
