# GLX Bitwise Keywords Reference
## Overview

```
GLX provides a set of bitwise keywords that allow direct manipulation of numeric values at the binary (bit) level. These keywords are designed for low-level operations, performance-sensitive logic, and precise data control. Bitwise operations in GLX are explicit, readable, and predictable, making them suitable for system programming, flag handling, and mathematical optimizations.
```

All bitwise keywords return a numeric result and can be used wherever expressions are allowed.

`_and_`
Description

Performs a bitwise AND operation between two values.
Each bit of src is compared with the corresponding bit of tar.
The resulting bit is 1 only if both bits are 1; otherwise, it is 0.
Syntax `_and_[src, tar]`

Purpose
Masking specific bits
Checking flags
Restricting values at the bit level

_or_
Description
Performs a bitwise OR operation between two values.
Each result bit becomes 1 if either the src bit or the tar bit is 1. Syntax `_or_[src, tar]`

Purpose
Combining flags
Enabling bit states
Merging binary values

_com_
Description
Performs a bitwise complement (NOT) operation on a value. All bits of the input value are flipped:

1 becomes 0
0 becomes 1

Syntax
`_com_[src]`

Purpose
Inverting binary values
Creating negative masks
Bit-level inversion logic

`_lsh_`
Description

Performs a bitwise left shift operation.

All bits of src are shifted left by tar positions.
Empty right-side bits are filled with 0.
Syntax
`_lsh_[src, tar]`

Purpose
Fast multiplication by powers of two
Bit positioning
Performance-optimized arithmetic
`_rsh_`
Description

Performs a bitwise right shift operation.
All bits of src are shifted right by tar positions.
Rightmost bits are discarded.

Syntax
`_rsh_[src, tar]`

Purpose
Fast division by powers of two
Extracting higher-order bits
Bit reduction operations

Usage Example
print(src=_and_[src, tar])
print(src=_or_[src, tar])
print(src=_com_[src])
print(src=_lsh_[src, tar])
print(src=_rsh_[src, tar])
