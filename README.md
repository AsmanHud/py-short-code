# Python Short Code
Welcome to a collaborative collection of Python tips and tricks aimed at competitive programming enthusiasts. This document aims to share general advice and specific tips/tricks on writing the shortest (and absolutely unreadable) code possible.
> (initially being written for Shorter Code challenges on Codingame)

## List of tips and tricks
### Shorter for loop syntax when counter unused
Whenever you need a for loop to do something multiple times, but you don't need the counter variable, you can use the following trick:
```py
for _ in' '*int(input())
for _ in range(int(input())) # longer traditional version
```
### List comprehension (LC) or map
When you need to apply a function to each element of the array, you can either use map or list comprehension. Both are good for different cases:
- Use map when use are passing the name of a function as argument (i.e. you don't need a lambda expression) AND the iterable passed to map is not complex (see example 2 below)
- Use list comprehension in other cases (LC tends to be better when code is complex)
- Remember that map returns a map object, and sometimes you will need to convert it to a usable data type. Even with explicit conversion (like using list()), map can be better than LC (see below)
```py
# Examples:
# 1 - use case for map
map(int,input().split())         # no conversion needed
list(map(int,input().split()))   # need to convert
[int(x)for x in input().split()] # map is better in both cases
# 2 - using a complex iterable: [input()for _ in' '*int(input())]
[sorted(input())for _ in' '*int(input())]
map(sorted,[input()for _ in' '*int(input())]) # LC is better, because we can embed the applied function into the iterable
# 3 - use case for list comprehension
[int(x)**2 for x in input()]
map(lambda x:int(x)**2,input()) # list comprehension is better because of lambda expression in map
```
So in general, if you are unsure which method is shorter, double-checking would be the best option.
