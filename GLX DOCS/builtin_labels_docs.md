# Builtin Labels Documentation

## General Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `print` | *any, end? | Prints all provided values. Supports core types + Array/Dictionary/Axis; errors on user-defined datatypes. If end exists, it prints it (currently using Debug formatting). Always ends with newline. |
| `typeof` | src | Returns type name of src as String. Expects exactly 1 argument total. |
| `cast_type` | value, type | Casts value to type. Errors if either missing. |
| `input` | prompt | Reads user input with a prompt. |

## Array Builtins

| Label | Arguments | Description |
|-------|-----------|-------------|
| `array_new` | — | Creates a new empty array. |
| `array_len` | src | Returns length of array src. |
| `array_is_empty` | src | Returns true if array src is empty. |
| `array_get` | src, idx | Returns element at index idx from array src. |
| `array_set` | src, idx, value | Sets element at idx in src to value. |
| `array_push` | src, value | Appends value to end of array src. |
| `array_pop` | src | Removes and returns last element of array src. |
| `array_insert` | src, idx, value | Inserts value into array src at index idx. |
| `array_remove` | src, idx | Removes and returns element at idx in src. |
| `array_clear` | src | Clears all elements of array src. |
| `array_clone` | src | Returns a shallow clone of array src. |
| `array_slice` | src, start, end | Returns slice of src from start to end. |
| `array_concat` | st, nd | Returns new array = a followed by b. |
| `array_reverse` | src | Reverses array src (in-place or returns reversed depending on impl). |
| `array_sort` | src | Sorts array src (rules depend on your impl). |
| `array_find` | src, value | Finds value in src (likely returns index or nil). |
| `array_contains` | src, value | Returns true if src contains value. |

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

## Firebase Builtins

Firebase integration provides authentication, real-time database, and cloud storage functionality.

### Firebase Common

| Label | Arguments | Description |
|-------|-----------|-------------|
| `fb_init` | project_id, api_key, db_url, storage_bucket | Initializes Firebase connection with project credentials. Returns Firebase handle for subsequent operations. |
| `fb_set_timeout` | fb, ms | Sets timeout in milliseconds for Firebase operations using the Firebase handle. |

### Firebase Authentication

| Label | Arguments | Description |
|-------|-----------|-------------|
| `fb_auth_signup_email` | fb, email, password | Creates new user account with email and password. Returns session handle on success. |
| `fb_auth_signin_email` | fb, email, password | Signs in existing user with email and password. Returns session handle with authentication tokens. |
| `fb_auth_signout` | session | Signs out user and invalidates the session handle. |
| `fb_auth_refresh` | fb, session | Refreshes authentication tokens for an existing session. Returns updated session handle. |
| `fb_auth_send_reset_email` | fb, email | Sends password reset email to specified email address. |
| `fb_auth_userinfo` | fb, session | Retrieves user information for authenticated session. Returns user data dictionary. |

### Firebase Realtime Database

| Label | Arguments | Description |
|-------|-----------|-------------|
| `fb_db_get` | fb, session, path | Retrieves data from database at specified path. Path uses Firebase path syntax (e.g., "users/123/profile"). |
| `fb_db_set` | fb, session, path, value | Sets data at specified path, replacing existing data. Value can be any JSON-serializable type. |
| `fb_db_update` | fb, session, path, patch | Updates specific fields at path without replacing entire object. Patch should be a dictionary of field updates. |
| `fb_db_push` | fb, session, path, value | Pushes new child entry to list at path with auto-generated key. Returns the generated key. |
| `fb_db_delete` | fb, session, path | Deletes data at specified path from database. |

### Firebase Cloud Storage

| Label | Arguments | Description |
|-------|-----------|-------------|
| `fb_storage_upload_file` | fb, session, local_path, remote_path, content_type | Uploads file from local_path to Firebase Storage at remote_path with specified content type (e.g., "image/png"). |
| `fb_storage_download_file` | fb, session, remote_path, local_path | Downloads file from Firebase Storage remote_path to local_path on filesystem. |
| `fb_storage_delete` | fb, session, remote_path | Deletes file at remote_path from Firebase Storage. |
| `fb_storage_get_metadata` | fb, session, remote_path | Retrieves metadata for file at remote_path (size, content type, timestamps, etc.). |
| `fb_storage_list` | fb, session, prefix | Lists all files in Storage with specified prefix path. Returns array of file information. |
| `fb_storage_get_download_url` | fb, session, remote_path | Gets public download URL for file at remote_path. URL can be used for direct downloads. |
| `fb_storage_exists` | fb, session, remote_path | Checks if file exists at remote_path in Firebase Storage. Returns boolean. |

### Firebase Usage Example

```
print(src="=== FIREBASE FULL TEST (20 METHODS) ===")

// ------------------------------
// 0) CONFIG (change these)
// ------------------------------
PROJECT_ID = "YOUR_PROJECT_ID"
API_KEY    = "YOUR_WEB_API_KEY"
DB_URL     = "https://YOUR_PROJECT_ID-default-rtdb.firebaseio.com"
BUCKET     = "YOUR_PROJECT_ID.appspot.com"

EMAIL      = "test@example.com"
PASS       = "12345678"

// test paths
DB_BASE    = "/__ex_firebase_test__"
DB_USER    = DB_BASE + "/user"
DB_MSGS    = DB_BASE + "/msgs"

REMOTE_BASE = "ex_test"
REMOTE_FILE = REMOTE_BASE + "/hello.txt"
LOCAL_FILE  = "./test_upload.txt"
LOCAL_DOWN  = "./downloaded_hello.txt"

print(src="--- Step 1: init ---")
fb = fb_init(
  project_id=PROJECT_ID,
  api_key=API_KEY,
  db_url=DB_URL,
  storage_bucket=BUCKET
)
print(src="fb_init ok")

print(src="--- Step 2: set timeout ---")
fb = fb_set_timeout(fb=fb, ms=20000)
print(src="fb_set_timeout ok")

// ------------------------------
// AUTH TESTS (6)
// ------------------------------
print(src="--- AUTH: signup (may fail if user exists) ---")
signup_res = fb_auth_signup_email(fb=fb, email=EMAIL, password=PASS)
print(src="signup_res:")
print(src=signup_res)

print(src="--- AUTH: signin ---")
sess = fb_auth_signin_email(fb=fb, email=EMAIL, password=PASS)
print(src="signin ok, session:")
print(src=sess)

print(src="--- AUTH: userinfo ---")
ui = fb_auth_userinfo(fb=fb, session=sess)
print(src="userinfo:")
print(src=ui)

print(src="--- AUTH: refresh ---")
ref = fb_auth_refresh(fb=fb, session=sess)
print(src="refresh response:")
print(src=ref)

print(src="--- AUTH: reset email (may require email config) ---")
reset_ok = fb_auth_send_reset_email(fb=fb, email=EMAIL)
print(src="reset_ok:")
print(src=reset_ok)

print(src="--- AUTH: signout ---")
so = fb_auth_signout(session=sess)
print(src="signout:")
print(src=so)


// ------------------------------
// RTDB TESTS (5)
// ------------------------------
print(src="--- RTDB: set ---")
ok_set = fb_db_set(
  fb=fb,
  session=sess,
  path=DB_USER,
  value=[&d,
    "name": "Danish",
    "lang": "EX",
    "ok": __TRUE__,
    "score": 101
  ]
)
print(src="db_set:")
print(src=ok_set)

print(src="--- RTDB: get ---")
user_val = fb_db_get(fb=fb, session=sess, path=DB_USER)
print(src="db_get user:")
print(src=user_val)

print(src="--- RTDB: update ---")
ok_up = fb_db_update(
  fb=fb,
  session=sess,
  path=DB_USER,
  patch=[&d, "score": 202, "active": __TRUE__]
)
print(src="db_update:")
print(src=ok_up)

print(src="--- RTDB: push ---")
msg_key = fb_db_push(
  fb=fb,
  session=sess,
  path=DB_MSGS,
  value=[&d, "text":"hello", "ts": 123]
)
print(src="db_push key:")
print(src=msg_key)

print(src="--- RTDB: delete push item ---")
ok_del_msg = fb_db_delete(fb=fb, session=sess, path=(DB_MSGS + "/" + msg_key))
print(src="db_delete msg:")
print(src=ok_del_msg)


// ------------------------------
// STORAGE TESTS (7)
// ------------------------------
print(src="--- STORAGE: exists before upload ---")
ex1 = fb_storage_exists(fb=fb, session=sess, remote_path=REMOTE_FILE)
print(src="exists_before:")
print(src=ex1)

// Make sure LOCAL_FILE exists:
// create it manually: echo "hello firebase" > test_upload.txt
print(src="--- STORAGE: upload file ---")
meta = fb_storage_upload_file(
  fb=fb,
  session=sess,
  local_path=LOCAL_FILE,
  remote_path=REMOTE_FILE,
  content_type="text/plain"
)
print(src="upload meta:")
print(src=meta)

print(src="--- STORAGE: get metadata ---")
m2 = fb_storage_get_metadata(fb=fb, session=sess, remote_path=REMOTE_FILE)
print(src="metadata:")
print(src=m2)

print(src="--- STORAGE: get download url ---")
url = fb_storage_get_download_url(fb=fb, session=sess, remote_path=REMOTE_FILE)
print(src="download url:")
print(src=url)

print(src="--- STORAGE: download file ---")
dl = fb_storage_download_file(
  fb=fb,
  session=sess,
  remote_path=REMOTE_FILE,
  local_path=LOCAL_DOWN
)
print(src="download ok:")
print(src=dl)

print(src="--- STORAGE: list prefix ---")
lst = fb_storage_list(fb=fb, session=sess, prefix=(REMOTE_BASE + "/"))
print(src="list result:")
print(src=lst)

print(src="--- STORAGE: delete file ---")
del_ok = fb_storage_delete(fb=fb, session=sess, remote_path=REMOTE_FILE)
print(src="delete ok:")
print(src=del_ok)

print(src="--- STORAGE: exists after delete ---")
ex2 = fb_storage_exists(fb=fb, session=sess, remote_path=REMOTE_FILE)
print(src="exists_after:")
print(src=ex2)

print(src="=== DONE: FIREBASE FULL TEST ===")

```

---

## Notes

- Arguments marked with `?` are optional
- Most operations return `nil` on failure or appropriate error values
- Handle types (file, socket, thread, process, etc.) are implementation-specific opaque values
- Firebase operations require valid authentication session except for initialization
- Firebase paths use forward slash notation (e.g., "users/123/data")
