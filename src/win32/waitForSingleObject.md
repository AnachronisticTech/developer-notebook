# WaitForSingleObject

Instead of waiting for a process to end by polling its exit code with `GetExitCodeProcess`, which might hang as explained above, use e.g. **WaitForSingleObject**, or a family member.

```kotlin
WaitForSingleObject(pi.hProcess, INFINITE)
val exitCode: DWORDVar = alloc()
val result = GetExitCodeProcess(pi.hProcess, exitCode.ptr).convert<Int>()
CloseHandle(pi.hProcess)
CloseHandle(pi.hThread)

return if (result == 0) { // If result is 0, GetExitCodeProcess failed
    -1
} else {
    exitCode.value.convert()
}
```

