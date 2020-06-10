# execv

The `int execv(const char *file, char *const argv[])` function is used to replace the current process by executing a file at the specified path with arguments given as a vector list.

```c
char* command = "/bin/ls";  // The file to execute

char* argv[4];              // The list of arguments to pass (size >= 2)
argv[0] = "ls";             // The first argument must be the file to execute
argv[1] = ".";              // Arguments to the command
argv[2] = "-al";            // Arguments to the command
argv[3] = NULL;             // The last argument must be the null terminating character

int result = execv(command, argv); // Replace the current process
// If result is -1, exec failed
// Code beyond this point will not execute unless exec failed
// If exec failed, errno can be checked to determine the cause
```

