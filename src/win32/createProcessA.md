# CreateProcessA

**CreateProcess** used to be the fundamental way to create a new process, used internally by higher level functions such as `ShellExecute`.

With the advent of **User Access Control** security, UAC, one needs to use **ShellExecute** (or family member) to run a process with elevated access.

Where the process to be started is a console subsystem process, it can often be more convenient to use the C++ standard library's **system** function, which uses the `cmd.exe` command interpreter to run a specified command, waits for that to end, and returns the process exit code.

As stated in [MSDN](https://msdn.microsoft.com/en-us/library/windows/desktop/ms682425(v=vs.85).aspx), `CreateProcessA`'s 2nd argument : `lpApplicationName` is playing the role of the command line to be executed. Unless `lpApplicationName` points to an exe in a directory, the system will look for it in the following order:

1. The directory from which the application loaded.
2. The current directory for the parent process.
3. The 32-bit Windows system directory. Use the GetSystemDirectory function to get the path of this directory
4. The 16-bit Windows system directory. There is no function that obtains the path of this directory, but it is searched. The name of this directory is System. The Windows directory. Use the GetWindowsDirectory function to get the path of this directory.
5. The directories that are listed in the PATH environment variable. Note that this function does not search the per-application path specified by the App Paths registry key. To include this per-application path in the search sequence, use the ShellExecute function.

Therefore, unless the second argument of `CreateProcessA` is in the form `{directory}/{executable_name}.{ext}`, you'll have to either :

1. Place executable_name in the same directory from which the application loaded
2. Place executable_name in the same directory of the parent process
3. Place executable_name in the Windows System32 directory : C:\Windows\System32
4. Place executable_name in the Windows directory : C:\Windows
5. Include the directory where executable_name is in the PATH

The second parameter in `CreateProcess` should be a writable buffer. If your executable path does not include command line arguments then put the executable path in the first parameter, and leave the second parameter `NULL`