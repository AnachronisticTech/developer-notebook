# system

The `int system(char* command)` function executes the specified shell command in a new process and waits for the process to complete. The return value is the exit code of the executed command. As such, it **cannot** be assumed that a value of `0` means success as this is dependent on the command. `system()` is implemented using [`fork()`](fork.md) and [`execl()`](./exec/execl.md).

```c
int system("ls");
```

If `command` is `null` then a return value of `0` indicates a shell is available on the system. A non-zero value indicates there is no available shell.

If a child process cannot be created, `system()` returns `-1` and the global [`errno`](./exec/errno.md) value is set.