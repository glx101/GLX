# EX Language Constants Reference

## Language / Runtime

| Constant | Value | Description |
|----------|-------|-------------|
| `__VERSION__` | `"0.1.0"` | Language version |
| `__LANG__` | `"EX"` | Language name |
| `__RUNTIME__` | `"EX_VM"` | Runtime environment |

## OS / Architecture

| Constant | Value | Description |
|----------|-------|-------------|
| `__OS__` | System-dependent | Operating system (e.g., "linux", "windows", "macos") |
| `__ARCH__` | System-dependent | CPU architecture (e.g., "x86_64", "aarch64") |
| `__FAMILY__` | System-dependent | OS family (e.g., "unix", "windows") |
| `__ABI__` | `"SYSV"` | Application Binary Interface |

## CPU

| Constant | Value | Description |
|----------|-------|-------------|
| `__CPU_BITS__` | System-dependent | CPU bit width (32 or 64) |
| `__CPU_CORES__` | System-dependent | Number of available CPU cores |
| `__CPU_CACHE_LINE__` | `64` | CPU cache line size in bytes |
| `__CPU_ENDIAN__` | `"LITTLE"` or `"BIG"` | CPU byte order |

## Memory / Pointer

| Constant | Value | Description |
|----------|-------|-------------|
| `__PTR_SIZE__` | System-dependent | Pointer size in bytes (typically 4 or 8) |
| `__WORD_SIZE__` | System-dependent | Word size in bytes (typically 4 or 8) |
| `__PAGE_SIZE__` | `4096` | Memory page size in bytes |
| `__MAX_INT__` | `170141183460469231731687303715884105727` | Maximum integer value (i128::MAX) |
| `__MIN_INT__` | `-170141183460469231731687303715884105728` | Minimum integer value (i128::MIN) |

## Time / Clock

| Constant | Value | Description |
|----------|-------|-------------|
| `__CLOCKS_PER_SEC__` | `1000000` | Clock ticks per second (1 MHz) |
| `__HAS_MONOTONIC_CLOCK__` | `true` | Monotonic clock availability |
| `__TIMER_RESOLUTION_NS__` | `1` | Timer resolution in nanoseconds |

## IO / File Descriptors

| Constant | Value | Description |
|----------|-------|-------------|
| `__PATH_SEP__` | System-dependent | Path separator (`"/"` or `"\\"`) |
| `__LINE_SEP__` | `"\n"` | Line separator |
| `__STDIN__` | `0` | Standard input file descriptor |
| `__STDOUT__` | `1` | Standard output file descriptor |
| `__STDERR__` | `2` | Standard error file descriptor |

## File Open Modes

| Constant | Value | Description |
|----------|-------|-------------|
| `__FILE_READ__` | `"r` | Open file for reading |
| `__FILE_WRITE__` | `"w"` | Open file for writing |
| `__FILE_APPEND__` | `"a"` | Open file for appending |
| `__FILE_RWC_` | `"rw"` | Create file if it doesn't exist |
| `__FILE_WRC__` | `"wr"` | Truncate file to zero length |

## Process / Signals

| Constant | Value | Description |
|----------|-------|-------------|
| `__HAS_FORK__` | Platform-dependent | Fork capability (true on Unix) |
| `__HAS_THREADS__` | `true` | Thread support availability |
| `__HAS_SIGNALS__` | `true` | Signal support availability |
| `__SIGNAL_TERM__` | `15` | Termination signal (SIGTERM) |
| `__SIGNAL_KILL__` | `9` | Kill signal (SIGKILL) |
| `__SIGNAL_INT__` | `2` | Interrupt signal (SIGINT) |
| `__SIGNAL_HUP__` | `1` | Hangup signal (SIGHUP) |
| `__SIGNAL_QUIT__` | `3` | Quit signal (SIGQUIT) |
| `__SIGNAL_STOP__` | `19` | Stop signal (SIGSTOP) |
| `__SIGNAL_CONT__` | `18` | Continue signal (SIGCONT) |

## Floating Point

| Constant | Value | Description |
|----------|-------|-------------|
| `__HAS_FPU__` | `true` | Floating point unit availability |
| `__FLOAT_RADIX__` | `2` | Floating point radix (base) |
| `__FLOAT_MANTISSA_BITS__` | `52` | Mantissa bits in float representation |
| `__FLOAT_MAX__` | `1.7976931348623157e308` | Maximum f64 value |
| `__FLOAT_MIN__` | `-1.7976931348623157e308` | Minimum f64 value |
| `__FLOAT_EPSILON__` | `2.220446049250313e-16` | Machine epsilon for f64 |
| `__FLOAT_INFINITY__` | `∞` | Positive infinity |
| `__FLOAT_NEG_INFINITY__` | `-∞` | Negative infinity |

## Type Constants

| Constant | Value | Description |
|----------|-------|-------------|
| `__INT__` | `"INTEGER"` | Integer type identifier |
| `__UINT__` | `"UINTEGER"` | Unsigned integer type identifier |
| `__FLOAT__` | `"FLOAT"` | Float type identifier |
| `__BIGINT__` | `"BIG_INTEGER"` | Big integer type identifier |
| `__BYTEU__` | `"BYTEU"` | Unsigned byte type identifier |
| `__BYTEI__` | `"BYTEI"` | Signed byte type identifier |
| `__STRING__` | `"STRING"` | String type identifier |
| `__CHAR__` | `"CHAR"` | Character type identifier |
| `__BOOL__` | `"BOOLEAN"` | Boolean type identifier |
| `__NIL__` | `"NIL"` | Nil/null type identifier |

## Container Types

| Constant | Value | Description |
|----------|-------|-------------|
| `__ARRAY__` | `"ARRAY"` | Array type identifier |
| `__DICT__` | `"DICTIONARY"` | Dictionary type identifier |
| `__AXIS__` | `"AXIS"` | Axis type identifier |

## Network Constants

| Constant | Value | Description |
|----------|-------|-------------|
| `__AF_INET__` | `2` | IPv4 address family |
| `__AF_INET6__` | `10` | IPv6 address family |
| `__SOCK_STREAM__` | `"tcp"` | TCP stream socket |
| `__SOCK_DGRAM__` | `"udp"` | UDP datagram socket |
| `__SOCK_RAW__` | `"raw"` | Raw socket |
| `__SHUT_RD__` | `0` | Shutdown read operations |
| `__SHUT_WR__` | `1` | Shutdown write operations |
| `__SHUT_RDWR__` | `2` | Shutdown read and write operations |
| `__IPPROTO_TCP__` | `6` | TCP protocol number |
| `__IPPROTO_UDP__` | `17` | UDP protocol number |
| `__IPPROTO_ICMP__` | `1` | ICMP protocol number |

## JSON Type Constants

| Constant | Value | Description |
|----------|-------|-------------|
| `__JSON_NULL__` | `"NULL"` | JSON null type |
| `__JSON_BOOL__` | `"BOOLEAN"` | JSON boolean type |
| `__JSON_NUMBER__` | `"NUMBER"` | JSON number type |
| `__JSON_STRING__` | `"STRING"` | JSON string type |
| `__JSON_ARRAY__` | `"ARRAY"` | JSON array type |
| `__JSON_OBJECT__` | `"OBJECT"` | JSON object type |

## Thread Constants

| Constant | Value | Description |
|----------|-------|-------------|
| `__THREAD_STACK_SIZE__` | `2097152` | Default thread stack size (2MB) |
| `__THREAD_MAX__` | `1024` | Maximum number of threads |

## Time Format Constants

| Constant | Value | Description |
|----------|-------|-------------|
| `__TIME_FMT_ISO8601__` | `"%Y-%m-%dT%H:%M:%S"` | ISO 8601 format |
| `__TIME_FMT_RFC3339__` | `"%Y-%m-%dT%H:%M:%S%z"` | RFC 3339 format |
| `__TIME_FMT_RFC2822__` | `"%a, %d %b %Y %H:%M:%S %z"` | RFC 2822 format |
| `__TIME_FMT_DATE__` | `"%Y-%m-%d"` | Date only format |
| `__TIME_FMT_TIME__` | `"%H:%M:%S"` | Time only format |
| `__TIME_FMT_DATETIME__` | `"%Y-%m-%d %H:%M:%S"` | Date and time format |

## HTTP Constants

### HTTP Methods

| Constant | Value | Description |
|----------|-------|-------------|
| `__HTTP_GET__` | `"GET"` | HTTP GET method |
| `__HTTP_POST__` | `"POST"` | HTTP POST method |
| `__HTTP_PUT__` | `"PUT"` | HTTP PUT method |
| `__HTTP_DELETE__` | `"DELETE"` | HTTP DELETE method |
| `__HTTP_PATCH__` | `"PATCH"` | HTTP PATCH method |
| `__HTTP_HEAD__` | `"HEAD"` | HTTP HEAD method |

### HTTP Status Codes

| Constant | Value | Description |
|----------|-------|-------------|
| `__HTTP_OK__` | `200` | OK |
| `__HTTP_CREATED__` | `201` | Created |
| `__HTTP_NO_CONTENT__` | `204` | No Content |
| `__HTTP_BAD_REQUEST__` | `400` | Bad Request |
| `__HTTP_UNAUTHORIZED__` | `401` | Unauthorized |
| `__HTTP_FORBIDDEN__` | `403` | Forbidden |
| `__HTTP_NOT_FOUND__` | `404` | Not Found |
| `__HTTP_SERVER_ERROR__` | `500` | Internal Server Error |

## Memory Alignment Constants

| Constant | Value | Description |
|----------|-------|-------------|
| `__ALIGN_1__` | `1` | 1-byte alignment |
| `__ALIGN_2__` | `2` | 2-byte alignment |
| `__ALIGN_4__` | `4` | 4-byte alignment |
| `__ALIGN_8__` | `8` | 8-byte alignment |
| `__ALIGN_16__` | `16` | 16-byte alignment |
| `__ALIGN_32__` | `32` | 32-byte alignment |
| `__ALIGN_64__` | `64` | 64-byte alignment |

## Math Constants

| Constant | Value | Description |
|----------|-------|-------------|
| `__PI__` | `3.141592653589793` | Pi (π) |
| `__E__` | `2.718281828459045` | Euler's number (e) |
| `__TAU__` | `6.283185307179586` | Tau (2π) |
| `__PHI__` | `1.618033988749895` | Golden ratio (φ) |

## Sorting Constants

| Constant | Value | Description |
|----------|-------|-------------|
| `__SORT_ASC__` | `"ASC"` | Ascending sort order |
| `__SORT_DESC__` | `"DESC"` | Descending sort order |

## Exit Codes

| Constant | Value | Description |
|----------|-------|-------------|
| `__EXIT_SUCCESS__` | `0` | Successful program termination |
| `__EXIT_FAILURE__` | `1` | Unsuccessful program termination |