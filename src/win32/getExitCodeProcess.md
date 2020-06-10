# GetExitCodeProcess

**GetExitCodeProcess** is used to check the exit code of a process. By convention in Windows, Unix and in C++, exit code 0 (e.g. as returned from `main`) denotes success. In C++ this value is available as the macro symbol `EXIT_SUCCESS` from `<stdlib.h>`. On other systems `EXIT_SUCCESS` needs not be 0, but in C++ exit code 0 always denotes success, possibly in addition to the value of `EXIT_SUCCESS`.

The Windows and Unix-land convention is that any other exit code denotes failure, but the only portable failure value in C++ is the one denoted by `EXIT_FAILURE`. In Windows this is conventionally the value 1. Unfortunately that conflicts with the value of a Windows error code, about “incorrect function” (as reported by `errlook.exe`). For this reason one may choose to use Windows' own general failure value `E_FAIL` to indicate a general failure, instead of using the portable but imperfect `EXIT_FAILURE`.

Two relevant differences between Windows and Unix-land:

- In Windows a non-zero exit code is often an error code that tells you something about the cause of failure. It can be passed to a tool such as Microsoft's **errlook** to get a textual description, the same as via the API function **FormatMessage**. In Unix-land process exit codes used as failure cause indications are much less common.
- In Unix-land tools can generally be relied on to indicate failure or success via the exit code. This is not so in Windows. Even many of the built-in and standard commands fail to do so.

Especially the latter point is important for use of `GetExitCodeProcess`. You need to know that the process you're checking, is one that produces a meaningful exit-code.

Also note well that the code **STILL_ACTIVE** is defined as a low number, as I recall around 270 or thereabouts, and can be produced by a process, so that it is not a reliable indicator of whether a process is still active or not. I.e., don't use `GetExitCodeProcess` to poll for a process to finish. Depending on the process & circumstances, such code might hang.