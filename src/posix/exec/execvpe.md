# execvpe

The `int execvpe(const char *path, char *const argv[])` function is used to replace the current process by executing a file on the PATH with arguments given as a vector list and environment parameters given as a vector list.

```c
char* command = "ls";  // The file on the path to execute

char* argv[4];         // The list of arguments to pass (size >= 2)
argv[0] = "ls";        // The first argument must be the file to execute
argv[1] = ".";         // Arguments to the command
argv[2] = "-al";       // Arguments to the command
argv[3] = NULL;        // The last argument must be the null terminating character
char* env[] = {};      // The list of environmental parameters

int result = execvp(command, argv, environ); // Replace the current process
// If result is -1, exec failed
// Code beyond this point will not execute unless exec failed
// If exec failed, errno can be checked to determine the cause
```

