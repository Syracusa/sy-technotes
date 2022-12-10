# How to set timeout with windows serial communication 

## Reference
+ https://learn.microsoft.com/en-us/windows/win32/api/winbase/ns-winbase-commtimeouts

## Set timeout function
```
    COMMTIMEOUTS timeouts = { 0 };
    timeouts.ReadIntervalTimeout = 0;
    timeouts.ReadTotalTimeoutMultiplier = 0;
    timeouts.ReadTotalTimeoutConstant = 100;; /* 100ms timeout per read operation */
    timeouts.WriteTotalTimeoutMultiplier = 0;
    timeouts.WriteTotalTimeoutConstant = 100; /* 100ms timeout per write operation */

    success = SetCommTimeouts(serial_comm.port, &timeouts);
```

## Struct COMMTIMEOUTS 
```
typedef struct _COMMTIMEOUTS {
  DWORD ReadIntervalTimeout;
  DWORD ReadTotalTimeoutMultiplier;
  DWORD ReadTotalTimeoutConstant;
  DWORD WriteTotalTimeoutMultiplier;
  DWORD WriteTotalTimeoutConstant;
} COMMTIMEOUTS, *LPCOMMTIMEOUTS;
```

### ReadIntervalTimeout
+ Inter-byte timeout in milliseconds

### ReadTotalTimeoutMultiplier
+ Per-byte timeout in milliseconds

### ReadTotalTimeoutConstant
+ Total timeout for read operation would be (ReadTotalTimeoutMultiplier * bytestoread) + ReadTotalTimeoutConstant

### WriteTotalTimeoutMultiplier
+  Per-byte timeout in milliseconds

### WriteTotalTimeoutConstant
+ Total timeout for write operation would be WriteTotalTimeoutMultiplier * bytestowrite) + WriteTotalTimeoutConstant