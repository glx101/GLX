# Builtin Labels Documentation

## General Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `print` | *any, end? | Prints all provided values. Supports core types + Array/Dictionary/Axis; errors on user-defined datatypes. If end exists, it prints it (currently using Debug formatting). Always ends with newline. |
| `typeof` | src | Returns type name of src as String. Expects exactly 1 argument total. |
| `cast_type` | value, type | Casts value to type. Errors if either missing. |
| `input` | prompt | Reads user input with a prompt. |

## Array Builtins

| Label              | Arguments               | Description                                                                                      |
|--------------------|-------------------------|--------------------------------------------------------------------------------------------------|
| `array_new`        | `dest`                  | Creates a new empty array and assigns it to `dest`. Returns `true`.                              |
| `array_len`        | `src`                   | Returns the length (`Int`) of array `src`.                                                       |
| `array_is_empty`   | `src`                   | Returns `true` if array `src` is empty, otherwise `false`.                                       |
| `array_get`        | `src, idx`              | Returns the element at index `idx` from array `src`. Supports negative indexing.                 |
| `array_set`        | `src, idx, value`       | Sets `value` at index `idx` in array `src`. Modifies array in-place. Returns `true`.             |
| `array_push`       | `src, value`            | Appends `value` to the end of array `src`. Returns `true`.                                       |
| `array_pop`        | `src`                   | Removes and **returns** the last element of array `src`.                                         |
| `array_insert`     | `src, idx, value`       | Inserts `value` at index `idx` in array `src`. Supports negative indexing. Returns `true`.       |
| `array_remove`     | `src, idx`              | Removes the element at index `idx` from array `src`. Supports negative indexing. Returns `true`. |
| `array_clear`      | `src`                   | Removes all elements from array `src`. Returns `true`.                                           |
| `array_clone`      | `src, dest`             | Creates a shallow copy of array `src` and assigns it to `dest`. Returns `true`.                  |
| `array_slice`      | `src, start, end, dest` | Copies slice `src[start..end]` into `dest`. Supports negative indices. Returns `true`.           |
| `array_concat`     | `src, tar, dest`        | Concatenates arrays `src` and `tar`, stores result in `dest`. Returns `true`.                    |
| `array_reverse`    | `src`                   | Reverses array `src` in-place. Returns `true`.                                                   |
| `array_sort`       | `src`                   | Sorts array `src` in-place. Supported types: `Int`, `UInt`, `Float`, `String`. Returns `true`.   |
| `array_find`       | `src, value`            | Searches for `value` in array `src`. Returns index if found, otherwise `nil`.                    |
| `array_contains`   | `src, value`            | Returns `true` if array `src` contains `value`, otherwise `false`.                               |
| `split_prompt_tok` | `src, dest`             | Splits a string prompt into tokens (respects double quotes) and stores result in `dest`. Returns `true`. |

## Directory Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `dir_create` | path | Creates directory at path. |
| `dir_remove` | path | Removes directory at path. |
| `dir_exists` | path | Returns true if path exists. |
| `dir_is_dir` | path | Returns true if path is a directory. |
| `dir_is_empty` | path | Returns true if directory at path is empty. |
| `dir_current` | — | Returns current working directory. |
| `dir_parent` | path | Returns parent directory of path. |
| `dir_change` | path | Changes current working directory to path. |
| `dir_open` | path | Opens directory and returns a handle. |
| `dir_close` | handle | Closes an opened directory handle. |
| `dir_read` | path | Reads directory entries at path (likely one level). |
| `dir_read_all` | path | Reads all entries at path (possibly recursive depending on impl). |
| `dir_iter` | path | Returns an iterator/handle to iterate directory entries. |
| `dir_walk` | path | Walks directory tree starting at path. |
| `dir_glob` | pattern | Returns paths matching glob pattern. |
| `dir_rename` | src, dst | Renames directory from src to dst. |
| `dir_move` | src, dst | Moves directory from src to dst. |
| `dir_copy` | src, dst | Copies directory from src to dst. |
| `dir_size` | path | Returns total size for directory at path. |
| `dir_permissions` | path | Returns permissions metadata for directory. |
| `dir_modified_time` | path | Returns last modified time for directory. |

## File Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `file_open` | path, mode? | Opens file at path with optional mode (e.g. "r", "w", etc.) and returns handle. |
| `file_close` | handle | Closes an open file handle. |
| `file_permissions` | path | Returns file permissions metadata. |
| `file_modified_time` | path | Returns file modified timestamp. |
| `file_created_time` | path | Returns file created timestamp. |
| `file_access_time` | path | Returns file last access timestamp. |
| `file_create` | path | Creates a file at path. |
| `file_read` | handle | Reads from file handle (likely chunk/line depending on impl). |
| `file_read_all` | handle | Reads entire file contents from handle. |
| `file_write` | handle, data | Writes data to file handle. |
| `file_append` | handle, data | Appends data to file handle. |
| `file_truncate` | handle, size | Truncates file to size. |
| `file_delete` | path | Deletes file at path. |
| `file_exists` | path | Returns true if file exists at path. |
| `file_size` | path | Returns size of file at path. |
| `file_move` | src, dst | Moves file from src to dst. |

## Math Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `math_abs` | src | Absolute value of src. |
| `math_cbrt` | src | Cube root. |
| `math_ceil` | src | Ceiling. |
| `math_cos` | src | Cosine. |
| `math_exp` | src | Exponential (e^x). |
| `math_floor` | src | Floor. |
| `math_log10` | src | Base-10 log. |
| `math_log` | src | Natural log. |
| `math_round` | src | Rounds to nearest integer. |
| `math_sin` | src | Sine. |
| `math_sqrt` | src | Square root. |
| `math_tan` | src | Tangent. |
| `math_pow` | st, nd | Power: a^b. |
| `math_min` | st, nd | Returns smaller of a and b. |
| `math_max` | st, nd | Returns larger of a and b. |

## String Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `str_len` | src | Length of string src. |
| `str_empty` | src | True if string is empty. |
| `str_clone` | src | Returns cloned copy of string. |
| `str_upper` | src | Uppercase string. |
| `str_lower` | src | Lowercase string. |
| `str_trim` | src | Trim whitespace. |
| `str_capitalize` | src | Capitalizes string (rules depend on impl). |
| `str_reverse` | src | Reverses string. |
| `str_concat` | st, nd | Concatenates a + b. |
| `str_compare` | st, nd | Compares two strings (likely -1/0/1 or bool depending on impl). |
| `str_contains` | src, sub | True if src contains substring sub. |
| `str_starts_with` | src, prefix | True if src starts with prefix. |
| `str_ends_with` | src, suffix | True if src ends with suffix. |
| `str_find` | src, sub | Finds sub in src (likely returns index or nil). |
| `str_count` | src, sub | Counts occurrences of sub in src. |
| `str_replace` | src, from, to | Replaces from with to inside src. |
| `str_slice` | src, start, end | Slices substring from start to end. |
| `str_split` | src, sep | Splits src by separator sep into array. |
| `str_join` | arr, sep | Joins string array arr with separator sep. |
| `str_hash` | src | Returns hash of string src. |

## Process Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `process_cwd` | — | Gets current working directory of process. |
| `process_set_cwd` | path | Sets current working directory to path. |
| `process_env_get` | key | Gets environment variable by key. |
| `process_env_set` | key, value | Sets environment variable. |
| `process_env_unset` | key | Unsets environment variable. |
| `process_id` | — | Returns current process ID. |
| `process_parent_id` | — | Returns parent process ID. |
| `process_group_id` | — | Returns process group ID. |
| `process_session_id` | — | Returns session ID. |
| `process_uptime` | — | Returns process uptime (implementation-defined). |
| `process_spawn` | cmd | Spawns a new process for command cmd, returns handle. |
| `process_exec` | cmd | Executes command cmd (often replaces current process depending on impl). |
| `process_is_alive` | handle | True if process handle is still alive. |
| `process_status` | handle | Returns process exit/status info. |
| `process_wait` | handle | Waits for process to finish. |
| `process_kill` | handle | Kills the process. |
| `process_signal` | handle, sig | Sends signal sig to process. |
| `process_suspend` | handle | Suspends process. |
| `process_resume` | handle | Resumes suspended process. |
| `process_exit` | code | Exits current process with exit code. |

## Dictionary Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `dict_new` | — | Creates a new empty dictionary. |
| `dict_len` | src | Returns number of entries in dictionary src. |
| `dict_is_empty` | src | True if src has no entries. |
| `dict_get` | src, key | Gets value for key (likely nil if missing depending on impl). |
| `dict_set` | src, key, value | Sets key to value. |
| `dict_remove` | src, key | Removes key from dict. |
| `dict_clear` | src | Clears dictionary. |
| `dict_clone` | src | Returns clone of dictionary. |
| `dict_contains_key` | src, key | True if dict has key. |
| `dict_contains_value` | src, value | True if dict contains value. |
| `dict_keys` | src | Returns array of keys. |
| `dict_values` | src | Returns array of values. |
| `dict_items` | src | Returns array of key/value pairs (format depends on impl). |
| `dict_merge` | st, nd | Merges dictionaries a and b (rules depend on impl). |
| `dict_update` | src, other | Updates src with entries from other. |
| `dict_pop` | src, key | Removes key and returns its value. |
| `dict_popitem` | src | Pops and returns one (key,value) item. |
| `dict_default` | src, key, default | Returns value for key, else returns default. |
| `dict_map` | src, op | Applies operation op to entries (depends on your callable/op system). |
| `dict_filter` | src, op, extra | Filters dict using op and optional extra input extra (depends on impl). |

## Memory Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `mem_layout` | size, align? | Creates a memory layout descriptor for allocation (size + optional alignment). |
| `mem_alloc` | layout | Allocates memory using layout, returns handle. |
| `mem_realloc` | handle, layout | Reallocates memory block to new layout. |
| `mem_free` | handle | Frees memory handle. |
| `mem_write_byte` | handle, offset, value | Writes a single byte at offset. |
| `mem_read_byte` | handle, offset | Reads a single byte at offset. |
| `mem_write` | handle, offset, data | Writes data (buffer/array) at offset. |
| `mem_read` | handle, offset, size | Reads size bytes from offset. |
| `mem_ptr` | handle | Returns raw pointer/address representation for the handle (impl-defined). |

## Thread Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `thread_spawn` | ms? | Spawns a thread (your impl decides what runs). Optional ms may configure timeout/delay/etc. |
| `thread_join` | handle | Joins thread by handle. |
| `thread_detach` | handle | Detaches thread. |
| `thread_is_alive` | handle | True if thread is alive. |
| `thread_id` | handle | Returns thread id. |
| `thread_kill` | handle | Attempts to kill thread. |
| `thread_park` | — | Parks current thread. |
| `thread_unpark` | handle | Unparks thread by handle. |
| `thread_sleep` | ms | Sleeps current thread for milliseconds. |
| `thread_yield` | — | Yields execution of current thread. |

## Time Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `time_now` | — | Current time (representation depends on your Value type). |
| `time_epoch` | — | Epoch time (likely seconds/ms since UNIX epoch depending on impl). |
| `time_monotonic` | — | Monotonic clock reading (good for durations). |
| `time_sleep` | ms | Sleeps for milliseconds. |
| `time_nanosleep` | ns | Sleeps for nanoseconds. |
| `time_utc` | — | Current UTC timestamp or datetime representation. |
| `time_local` | — | Current local timestamp or datetime representation. |
| `time_year` | ts, utc? | Extract year from timestamp ts; if utc is provided, uses UTC mode. |
| `time_month` | ts, utc? | Extract month. |
| `time_day` | ts, utc? | Extract day. |
| `time_hour` | ts, utc? | Extract hour. |
| `time_minute` | ts, utc? | Extract minute. |
| `time_second` | ts, utc? | Extract second. |
| `time_millisecond` | ts, utc? | Extract millisecond. |
| `time_format` | ts, fmt, utc? | Format timestamp ts using format string fmt. |
| `time_parse` | text, fmt, utc? | Parse datetime string text using format fmt. |
| `time_duration_new` | secs, nanos | Creates duration from seconds + nanoseconds. |
| `time_duration_add` | a1, b1 | Adds two durations (or duration-like values). |
| `time_duration_sub` | a1, b1 | Subtracts two durations. |
| `time_diff` | a1, b1 | Difference between two timestamps/time values (returns duration-like). |

## Network Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `net_socket_new` | type | Creates a new socket of specified type (e.g., TCP, UDP). Returns socket handle. |
| `net_socket_close` | handle | Closes an open socket handle. |
| `net_socket_bind` | ip, port, type | Binds a socket to an IP address and port with specified type. |
| `net_socket_listen` | handle, backlog? | Puts socket in listening mode with optional backlog (default 128). |
| `net_socket_accept` | handle | Accepts incoming connection on listening socket. Returns new socket handle for client. |
| `net_socket_connect` | ip, port | Connects socket to specified IP address and port. |
| `net_socket_send` | handle, data | Sends data through connected socket. |
| `net_socket_recv` | handle, size | Receives up to size bytes from socket. |
| `net_socket_sendto` | handle, ip, port, data | Sends data to specified IP/port (UDP-style). |
| `net_socket_recvfrom` | handle, size | Receives data and sender address from socket (UDP-style). |
| `net_socket_set_timeout` | handle, ms | Sets timeout in milliseconds for socket operations. |
| `net_socket_set_blocking` | handle, on | Sets socket blocking mode (true/false). |
| `net_socket_shutdown` | handle, how | Shuts down socket for reading, writing, or both based on how parameter. |
| `net_socket_peer` | handle | Returns peer (remote) address information for connected socket. |
| `net_socket_local` | handle | Returns local address information for socket. |
| `net_socket_set_reuseaddr` | handle, on | Sets SO_REUSEADDR socket option (allows address reuse). |
| `net_socket_set_nodelay` | handle, on | Sets TCP_NODELAY socket option (disables Nagle's algorithm). |
| `net_socket_set_keepalive` | handle, on | Sets SO_KEEPALIVE socket option (enables TCP keepalive). |
| `net_socket_get_error` | handle | Gets the last error code for the socket. |
| `net_poll` | handles, timeout_ms | Polls multiple socket handles for events with timeout. |
| `net_select` | read, write, except, timeout_ms | Selects sockets ready for read/write/exception with timeout. |
| `net_dns_lookup` | host | Performs DNS lookup for hostname, returns IP address(es). |
| `net_ip_parse` | ip | Parses IP address string into structured format. |
| `net_ip_is_ipv4` | ip | Returns true if IP address is IPv4. |
| `net_ip_is_ipv6` | ip | Returns true if IP address is IPv6. |
| `net_http_get` | url, headers? | Performs HTTP GET request to URL with optional headers. |
| `net_http_post` | url, headers?, body | Performs HTTP POST request with optional headers and body data. |
| `net_interface_list` | — | Returns list of network interfaces on the system. |
| `net_interface_up` | name | Checks if network interface with given name is up/active. |
| `net_mac_address` | name | Returns MAC address for network interface with given name (Linux only). |
| `net_addr` | host, port | Creates a network address structure from host and port. |

## JSON Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `json_parse` | text | Parses JSON string and returns corresponding Value (Dictionary, Array, etc.). |
| `json_stringify` | value | Converts Value to JSON string representation. |
| `json_validate` | text | Validates if text is valid JSON. Returns true/false or error. |
| `json_pretty` | text, indent? | Pretty-prints JSON string with optional indentation level. |
| `json_minify` | text | Minifies JSON string by removing unnecessary whitespace. |
| `json_get` | obj, path | Gets value at path in JSON object (e.g., "a.b[0].c"). |
| `json_set` | obj, path, value | Sets value at path in JSON object. |
| `json_has` | obj, path | Returns true if path exists in JSON object. |
| `json_remove` | obj, path | Removes value at path from JSON object. |
| `json_keys` | obj | Returns array of keys from JSON object. |
| `json_values` | obj | Returns array of values from JSON object. |
| `json_type` | value | Returns JSON type of value as string ("object", "array", "string", etc.). |
| `json_merge` | st, nd | Merges two JSON objects a and b. |
| `json_clone` | value | Creates a deep clone of JSON value. |
| `json_equal` | st, nd | Checks if two JSON values are equal. |
| `json_number` | value | Converts value to JSON number type. |
| `json_string` | value | Converts value to JSON string type. |
| `json_bool` | value | Converts value to JSON boolean type. |
| `json_array` | value | Converts value to JSON array type. |
| `json_dictionary` | value | Converts value to JSON object/dictionary type. |

## Random Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `random_int` | min, max | Generates a random integer between min and max (inclusive). |
| `random_float` | min, max | Generates a random floating-point number between min and max. |
| `random_bool` | — | Generates a random boolean value (true or false). |
| `random_choice` | src | Randomly selects and returns one element from array src. |
| `random_bytes` | size | Generates size random bytes, returns as byte array or similar. |

## Exit & Process Execution

| Label | Arguments | Description |
|-------|-----------|-------------|
| `exit_code` | code | Exits the current running program with specified exit code. |
| `imperium` | program, args | Executes external program with arguments. Returns array: [exitcode, output, status, ok, pending, err]. |

### Imperium Usage Example

```
res = imperium(
    program="ls",
    args=["-l", "-la"]
)

exitcode = array_get(src=res, idx=0)
output   = array_get(src=res, idx=1)
status   = array_get(src=res, idx=2)
ok       = array_get(src=res, idx=3)
pending  = array_get(src=res, idx=4)
err      = array_get(src=res, idx=5)
```
