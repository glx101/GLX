# GLX Reference Docs: `class` (Object-Oriented Syntax)

This document explains how classes work in GLX using your `person` example: how to define a class, 
how the constructor works, how to create an object, and how to access methods (functions) correctly.

## 1) Class Definition

In GLX, a class is defined using:
```
implement ClassName
{
    // constructor + methods
}
```

Example:
```
implement person
{
    constructor(name=uname, age=uage) {
        name = uname
        age = uage
    }

    print_name() {
        print(src="danishk Sinha")
    }

    greeting() {
        print(src="Hello Mr. " + name + " How are You")
    }

    do_this(job=new_job) {
        print(src=name+", Working New JOB : "+new_job)
        return true
    }
}
```

**What this means**
* `implement person { ... }` creates a class named person.
* Inside the class:
   * `constructor(...) { ... }` runs automatically when an object is created.
   * Other blocks like `print_name()`, `greeting()`, `do_this()` are class methods.

## 2) Constructor

**Syntax**
```
constructor(param1=local1, param2=local2) {
    field1 = local1
    field2 = local2
}
```

**In your code**
```
constructor(name=uname, age=uage) {
    name = uname
    age = uage
}
```

**Meaning:**
* When you create an object, GLX takes the provided values (`name`, `age`)
* Internally, they are received into temporary/local variables (`uname`, `uage`)
* Then you store them into the class fields: `name` and `age`

So the constructor is doing the "object setup".

## 3) Object Creation (`new`)

**Syntax**
```
obj = new ClassName::(arg=value, arg2=value2)
```

**Your example**
```
danishk = new person::(name="danishk", age=21)
```

This creates a new person object, stores it in variable `danishk`, and runs the constructor with:
* `name = "danishk"`
* `age = 21`

## 4) Accessing Class Methods (Functions)

**Rule (your language design)**

✅ You can access only functions/methods after creating an object.
❌ You cannot access the constructor or class variables directly from outside.

**Correct access pattern**
```
objectName . className . functionName()
```

**Your calls:**
```
danishk.person.print_name()
danishk.person.greeting()
print(src=danishk.person.do_this(job="CLEANING"))
```

**Explanation**
* `danishk` → the object you created
* `.person` → the class scope inside that object
* `.print_name()` / `.greeting()` / `.do_this()` → calling class methods

## 5) Encapsulation: Class Variables Not Accessible

Your note is correct:
```
// print(src=danishk.person.name) error
// cannot access class variable and constructor directly
```

**What this enforces in GLX**
* Fields like `name` and `age` are private (internal) by default.
* Outside code can't do: `obj.person.name`
* Outside code can only call class methods:
   * `obj.person.greeting()`
   * `obj.person.do_this(...)`

This is a clean OOP rule: data is protected, behavior is public.

## 6) Method Return Values

Methods can return values using `return`.

**Example:**
```
do_this(job=new_job) {
    print(src=name+", Working New JOB : "+new_job)
    return true
}
```

And you can print the returned value:
```
print(src=danishk.person.do_this(job="CLEANING"))
```

Output shows it returns `true`.

## 7) Full Example (As Official Reference Snippet)
```
implement person
{
    constructor(name=uname, age=uage) {
        name = uname
        age = uage
    }

    print_name() {
        print(src="danishk Sinha")
    }

    greeting() {
        print(src="Hello Mr. " + name + " How are You")
    }

    do_this(job=new_job) {
        print(src=name+", Working New JOB : "+new_job)
        return true
    }
}

danishk = new person::(name="danishk", age=21)

danishk.person.print_name()
danishk.person.greeting()
print(src=danishk.person.do_this(job="CLEANING"))

// ❌ Not allowed in GLX (fields + constructor not accessible directly)
// print(src=danishk.person.name)
```

If you want, I can also write a "Class Rules" mini-section for your GLX docs (bullet points like: 
constructor rules, method call syntax, privacy rules), in the same official style as your reference docs.