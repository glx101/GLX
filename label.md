

# Labels
## There Is No Concept Of Functions in glx Language, Why?, because

```
i do'nt like functions, when yo do print(src=""), behind the scene, you are jumping on a label.

```

labels are similar to functions.

## How to call a label
```
<label name> <open-paren> <name-of-param> = <assign-value> <close-paren>

Example:

do_this(src=some, tar=other)
```

## Input Label
```
input(prompt="Enter Name of Your Friend")
```

## Stander Library
```
There are almost 200 stander labels
```

## Declaring  A Label
```
test.glx:

label do_this() {

}


run using command:
./test.glx

but wait, an error occurred:

./labels.glx
[line 2] Error at 'do_this': Expected 'visit' keyword after label
```

## What is visit
```

visit and visible are options which hold data to make some variables static.

Example:
visible my_block(
    counter = 0,
    appName = "MyApp",
    maxUsers = 100
)

Because after execution of the program, all data from that function which was running is lost, but visible is a way to make data static for that function.
Static means after function discharge, values and variables are not removed from memory.
```

How to declare a function

```
/*
    Author : Danishk Sinha
    ./src/Test/labels.glx
*/

visible inc (
    count = 0
)

label visit[inc] count_func() {
    count++
    print(src=count)
}

label visit[] main() {
    count_func()
    count_func()
    count_func()
    count_func()
}

main()

PATH=[/home/danishk/Downloads/glx-LANGUAGE-main/glx-LANGUAGE-main] USER=[danishk]% ./src/Test/labels.glx
1
2
3
4
PATH=[/home/danishk/Downloads/glx-LANGUAGE-main/glx-LANGUAGE-main] USER=[danishk]% 
```

Second Example

```
/*
    Author : Danishk Sinha
    src/Test/labels.glx
*/

visible inc (
    count = 0
)

label visit[inc] count_func() {
    print(src=++count)
}

label visit[] main() {
    count_func()
    count_func()
    count_func()
    count_func()
}

main()

PATH=[/home/danishk/Downloads/glx-LANGUAGE-main/glx-LANGUAGE-main] USER=[danishk]% ./src/Test/labels.glx
1
2
3
4
PATH=[/home/danishk/Downloads/glx-LANGUAGE-main/glx-LANGUAGE-main] USER=[danishk]%
```


# Label Design
* mandatory <br>
^ optional

```

*label *visit[^visible, ^visible] <*label-name> <*left-paren> <^args> <*right-paren> <&left-curly> <*right-curly>

```

## Control Flow Label
```
Take some time and Digest it:

count = 0

label @repeat 
{
    if (count < 10) {
        count++
        print(src=count)
        jump repeat
    } else {
        jump done
    }
}


label @done {
    if (count < 10) {
        jump repeat
    } else {
        pass
    }
}

jump done

PATH=[/home/danishk/Downloads/glx-LANGUAGE-main/glx-LANGUAGE-main] USER=[danishk]% ./src/Test/labels.glx
1
2
3
4
5
6
7
8
9
10
PATH=[/home/danishk/Downloads/glx-LANGUAGE-main/glx-LANGUAGE-main] USER=[danishk]% 
```


## Explanation
```
count = 0

A variable count starts at 0.

2) label @repeat { ... }

This label is the loop body.

label @repeat 
{
    if (count < 10) {
        count++
        print(src=count)
        jump repeat
    } else {
        jump done
    }
}

What happens inside:

If count < 10:

count++ → increases count by 1

print(src=count) → prints the new value

jump repeat → jumps back to the start of @repeat (so it repeats)

Else (count >= 10):

jump done → exits the loop and goes to @done

So @repeat keeps running until count reaches 10.

That’s why output becomes:
1 2 3 4 5 6 7 8 9 10

3) label @done { ... }

This label is a final guard / exit point.

label @done {
    if (count < 10) {
        jump repeat
    } else {
        pass
    }
}

Meaning:

If somehow you arrive at @done while count is still less than 10, it sends you back to repeat.

Otherwise, it does pass (means: do nothing / end safely).

So @done ensures:
    if loop isn’t finished, go back
    if loop is finished, stop

4) jump done

At the bottom:

jump done


This is the entry point of the program.
The program starts by jumping to @done.
@done checks count.
Since count = 0, it says count < 10 → jump repeat.

Then @repeat runs the loop and prints 1..10.
When count becomes 10, @repeat jumps back to done.
@done sees count < 10 is false, so it pass and the program ends.

In simple words
@repeat = “do the work and repeat”
@done = “check if we’re finished”
jump = flow control (like goto)
Result = prints 1 to 10 exactly like your output.
```

## Return
```
return is used to return value from function.

label visit[] count_func() {
    print(src="1")
    print(src="2")
    return nil
    print(src="3")
    print(src="4")
}

count_func()

/*
    output
    1
    2
*/

```

>> When you write `return`, then you have to return some value, If you do not have to return any value, but you want to return without any value, then return nil as (void), do not use `return`, use `return nil.`