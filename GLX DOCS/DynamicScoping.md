# Dynamic Scoping

The **Dynamic Scoping** (`_grand_parent_`) is a dynamic scoping control construct in GLX. It allows code inside a nested block or label to define or modify variables and labels in an ancestor (parent) scope, instead of the current local scope.

In simple terms:
It lets you "push" variables or labels upward into outer scopes.

## Syntax
```glx
_grand_parent_[level N] {
    // statements
}
```

## Parameters

* `level`: a positive integer
   * `level 1` → direct parent scope
   * `level 2` → parent of the parent
   * `level 3` → three levels up, and so on

The block body is executed normally, but all definitions inside it are applied to the selected ancestor scope.

## Full Example
```glx
label visit[] main()
{
    _grand_parent_[level 1] {
        name = "danishk"
    }

    label visit[] nest() {
        _grand_parent_[level 2] {
            age = 21

            label visit[] greet(name=uname) {
                print(src="Hello Mr."+uname+" How are You")
            }
        }
    }

    nest()
}

main()
print(src=name)
print(src=age)

greet(name="danishk")
```

## Step-by-Step Explanation

### 1. Inside `main()`
```glx
_grand_parent_[level 1] {
    name = "danishk"
}
```

* `level 1` refers to the direct parent scope of `main()`
* The variable `name` is not stored in `main()`'s local scope
* Instead, it is written into the parent (outer) scope
* As a result, `name` becomes globally accessible after `main()` finishes

This is why:
```glx
print(src=name)
```

works outside `main()`.

### 2. Inside `nest()`
```glx
_grand_parent_[level 2] {
    age = 21
    label visit[] greet(name=uname) { ... }
}
```

* `level 2` means two scopes above `nest()`
* Both:
   * `age = 21`
   * the `greet` label
* are injected into that ancestor scope

This effectively "exports" them out of the nested label.

So after `nest()` is called:
```glx
print(src=age)
greet(name="danishk")
```

both execute successfully.

## Why This Is Useful

The Grand Parent Block is useful when:

* You want nested labels to create or expose values globally
* You need controlled dynamic scoping, not full global variables
* You want to avoid returning large structures just to pass data upward
* You want to register labels (functions) conditionally or dynamically

It provides precise control over where a definition lives.

## Scope Behavior Summary

| Level | Target Scope |
|-------|--------------|
| `level 1` | Direct parent |
| `level 2` | Parent of parent |
| `level N` | Nth ancestor |

All assignments and label definitions inside the block are applied only to that target scope.

## Important Notes

* If the specified ancestor level does not exist, a runtime error should be raised.
* `_grand_parent_` affects definitions, not just variable values.
* Code inside the block still executes in order; only the storage location changes.
* This is intentional dynamic scoping, not accidental global leakage.