# fork

The `int fork()` function creates a new process as a duplicate of the current process. The return value indicates the status of the child process creation.

```kotlin
val pid: Int = fork()
when {
    pid == 0 -> {    // If result is 0, fork succeeded and we are the child
        // Code run only by child
    }
    pid < 0  -> {    // If result < 0, fork failed and we are the parent
        // Code run only by parent
    }
    else -> {        // If result > 0, fork succeeded and we are the parent
        // Code run only by parent
    }
}
// Code run by:
// - Parent
// - Child if did not return or exit already
```

