# Running a list of commands

## Problem
You want to run a list of commands in order, sometimes in parallel. Sometimes you want to run a command only if another command succeeds or fails.

## Solution
To run more than one command in order, simply type each command in the order you want them to run, separating them with a semicolon `;`

```
    echo 1; echo 2; echo 3;
    > 1
    > 2
    > 3
```

To run a command only if the previous ones succeed, we can use `&&`

```
    ls <file> && rm <file> -rf
```

To run a command only if the previous ones fail, we use `||`
```
    ls file &> /dev/null || echo "File not exist"
    > File not exist
```

To run several commands in parallel, you can run them as background process using `&` then `wait`

```
process1 &
process2 &
process3 &
process4 &
wait
process5 &
process6 &
process7 &
process8 &
wait
```

If you want to make sure that all processes succeeds together, you can use npm package [`parallelshell`](https://github.com/keithamus/parallelshell)

```
    parallelshell "echo 1" "echo 2" "echo 3"
```

# References
* [http://stackoverflow.com/questions/19543139/bash-script-processing-commands-in-parallel](http://stackoverflow.com/questions/19543139/bash-script-processing-commands-in-parallel)
