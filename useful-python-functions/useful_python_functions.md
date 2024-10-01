# Useful python functions

## map(fun, iter)

`map()` function returns a map object (which is an iterator)
of the result after applying the given function to each item of a given iterable
(list, tuple, etc).

Useful when used with `.join()` where **The iterable you pass has to have all items where the
return type is *str*. You can utilize map() here.

Example: You want to convert a list of numbers and merge them all into one bigger number.

```
number_list = [1, 2, 3]
print(f"combined number: {"".join(map(str, number_list))}")
```