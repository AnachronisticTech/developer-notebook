# execl

The `int execl(const char *path, const char *arg, ...)` function is used to replace the current process by executing a file at the specified path with arguments given as a varargs list.

```c
char* command = "/bin/ls";  // The file to execute

char* p1 = "ls";            // The first argument must be the file to execute
char* p2 = ".";             // Arguments to the command
char* p3 = "-al";           // Arguments to the command
char* p4 = NULL;            // The last argument must be the null terminating character

int result = execl(command, p1, p2, p3, p4); // Replace the current process
// If result is -1, exec failed
// Code beyond this point will not execute unless exec failed
// If exec failed, errno can be checked to determine the cause
```

