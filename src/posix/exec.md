# exec

The `int exec()` family of functions replace the current process with a new one.

## Variants

```c
int execl(const char *path, const char *arg, ...);
int execlp(const char *file, const char *arg, ...);
int execle(const char *path, const char *arg, ..., char * const envp[]);
int execv(const char *path, char *const argv[]);
int execvp(const char *file, char *const argv[]);
int execvpe(const char *file, char *const argv[], char *const envp[]);
```


| Function                         | Description                                                  |
| -------------------------------- | ------------------------------------------------------------ |
| [`execl()`](./exec/execl.md)     | execute file at specified path with arguments given as a varargs list |
| [`execlp()`](./exec/execp.md)    | execute a file on the PATH with arguments given as a varargs list |
| [`execle()`](./exec/execle.md)   | execute file at specified path with arguments given as a varargs list and environment parameters given as a vector list |
| [`execv()`](./exec/execv.md)     | execute file at specified path with arguments given as a vector list |
| [`execvp()`](./exec/execvp.md)   | execute file on the PATH with arguments given as a vector list |
| [`execvpe()`](./exec/execvpe.md) | execute file on the PATH with arguments given as a vector list and environment parameters given as a vector list |

## Failure

If an exec variant fails to execute successfully, the currently executing process will not be replaced, and the global `errno` constant will be updated with an error value that indicates the cause of the problem. The full list of errors can be viewed [here](./exec/errno.md).