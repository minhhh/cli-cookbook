# Generating random numbers
## Problem

You want to generate a random number. Or maybe you want to generate a random hash to be used as password.

## Solution

Reading from `/dev/random` or `/dev/urandom` is the way to generate randomness in Linux.

To generate random number we do it like so
```
    # generate one byte of random, i.e. 0 to 255
    od -A n -t d -N 1 /dev/urandom
    > 87

    # generate 2 byte of random, i.e. 0 to 65535
    od -A n -t d -N 2 /dev/urandom
    > 30651
```

Generate random password or hash

```
    # From your current date, obviously not very random if you generate several in a row. Take 32 characters only
    date +%s | sha256sum | base64 | head -c 32 ; echo

    # another way to use date
    date | md5sum

    # another way is to use the existing openssl if you have it in your system
    openssl rand -base64 32

    # get random from /dev/urandom
    cat /dev/urandom | tr -dc _A-Z-a-z-0-9 | head -c${1:-32};echo;
```




