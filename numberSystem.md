# 🔢 Numeric Literals in GLX

## Binary, Hexadecimal, and Octal Numbers

GLX supports multiple numeric bases in addition to standard decimal numbers. This allows developers to write low-level, system-oriented, and bit-precise code in a clear and readable way. All numeric literals—regardless of their base—are internally converted into a single integer value, ensuring consistent behavior across arithmetic and printing operations.

---

## 📘 Supported Number Systems

GLX supports the following numeric formats:

| Number System | Prefix | Base | Digits Used |
|---------------|--------|------|-------------|
| Decimal       | (none) | 10   | `0–9`       |
| Binary        | `0b`   | 2    | `0, 1`      |
| Octal         | `Oo`   | 8    | `0–7`       |
| Hexadecimal   | `0x`   | 16   | `0–9, A–F`  |

---

## 🧮 Binary Numbers (`0b`)

Binary numbers are written using the `0b` prefix and consist only of `0` and `1`. They are commonly used in bitwise operations, flags, and low-level logic.

**Example**
```glx
binExample = 0b101010
print(src=binExample)
```

**Output**
```
42
```

---

## 🧮 Octal Numbers (`Oo`)

Octal numbers use the `Oo` prefix and digits from `0` to `7`. Octal representation is useful in permission flags, legacy systems, and compact numeric encoding.

**Example**
```glx
octalExample = Oo52
print(src=octalExample)
```

**Output**
```
42
```

---

## 🧮 Hexadecimal Numbers (`0x`)

Hexadecimal numbers use the `0x` prefix and digits `0–9` and `A–F`. Hex values are widely used in memory addresses, color codes, cryptography, and system programming.

**Example**
```glx
hexExample = 0x2A
print(src=hexExample)
```

**Output**
```
42
```

---

## ➕ Arithmetic Between Different Bases

In GLX, numbers from different bases can be mixed freely in arithmetic expressions. All values are automatically converted to their integer form before evaluation.

**Example**
```glx
sum = 0b101010 + Oo52
print(src=sum)
```

**Output**
```
84
```

✔ No casting required  
✔ No precision loss  
✔ No base conflicts

---

## 🔄 Internal Representation

Although numbers may be written in different bases, GLX internally stores all numeric literals as **integers**. This means:

* Printing always shows the decimal value
* Arithmetic behaves consistently
* Bitwise operations work naturally
* Base is only a syntax feature, not a type

---

## ⚠️ Notes & Rules

* Prefixes are **case-sensitive**
* Invalid digits for a base will raise a runtime error
* Leading zeros do not affect value
* Negative values are supported:
```glx
x = -0x2A
y = -0b101010
```

---

## ✅ Complete Example
```glx
hexExample   = 0x2A
binExample   = 0b101010
octalExample = Oo52

print(src=hexExample)
print(src=binExample)
print(src=octalExample)

sum = 0b101010 + Oo52
print(src=sum)
```

**Output**
```
42
42
42
84
```

---

## 🏁 Summary

* GLX supports **Binary**, **Octal**, and **Hexadecimal** literals
* All bases resolve to a single **integer** type
* Arithmetic operations work seamlessly across bases
* Output is always displayed in **decimal** format