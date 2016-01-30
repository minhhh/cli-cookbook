# Simulating user inputs

## Problem
Some programs require user to enter certain command before proceeding, we want to be able to send input to those programs automatically.

## Solution
The `expect` program can be used for this purpose. It will detect certain text that the program output such as a question, or a prompt, then it sends the the texts that we've prepares to the program.

For instance, send ssh password automatically

```
    expect -c "ssh abc@10.0.0.10\n ;  expect password: ; send mypassword\n ; interact "
```
