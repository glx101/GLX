
# Array, Axis, Dictionary

Now, beyond primitive data types, we have three data structures: array, axis, and dictionary. We need to remember three prefixes: &a, &l, and &d. &a is for creating an axis, &l for creating a list, and &d for creating a dictionary. [&d, "key": "value", "key2": "value2"], [&a, 555, 4, 33, 55, 66]. Remember that axis elements must have the same data type; axis does not allow mixed data types. The array, which starts with [&l], allows mixed data types. Arrays, axes, and lists are all dynamic, meaning you don't need to specify the size.

## Array
### Dynamic Size, Dynamic Type

```

[&l, 3, 4, 5, 44, "danishk", true, 44.44, false]

```

## Axis
### Immutable, FIx Type

```

[&a, 2, 3, 4, "false", true] // error
[&a, "danishk", "alice", "bob"] // will run
[&a, 744, 67, 44, 88, 90.9] // error
[&a, 744, 67, 44, 88, 90] // will run

```

## Dictionary
### Dynamic Size, Dynamic Type

```
some = [&d, "key": 101, "key2": false, "key3": 559.99]

print(src=some)

dict2 = [&d, "keyN" : some]
print(src=dict2["keyN"]["key2"])


PATH=[/home/danishk/Downloads/GLX/GLX-main] USER=[danishk]% ./src/Test/binary.glx
{key3: Float(559.99), key: Int(101), key2: Bool(false)}
false
PATH=[/home/danishk/Downloads/GLX/GLX-main] USER=[danishk]% 

```

## access array, axis and dict both three members abd variants using []