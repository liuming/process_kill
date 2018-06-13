# ProcessKill
ProcessKill is a specification to sent signal to running software processes in different ways.

One obvious use case is to terminate processes gracefully, if failed, then forcefully kill them.

Example:

1. Sent `QUIT` signal 6 times, at interval of 1,2,3,5,8,13 seconds in between
2. If the previous attempts failed, send `TERM` signal 5 times, one right after another
3. If the previous attempts failed, sent `KILL` signal 3 times, at intervals of 5 seconds in between

```yaml
---
- signal: QUIT
  interval:
  - 1
  - 2
  - 3
  - 5
  - 8
  - 13
- signal: TERM
  max_retry: 5
- signal: KILL
  max_retry: 3
  interval: 5
```
