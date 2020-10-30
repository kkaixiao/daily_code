
This problem was asked by **Jane Street**. Difficulty: **Medium**

```cons(a, b)``` constructs a pair, and ```car(pair)``` and ```cdr(pair)``` returns the first and last element of that pair. For example, ```car(cons(3, 4))``` returns 3, and ```cdr(cons(3, 4))``` returns 4.

Given this implementation of cons:

```python3
def cons(a, b):
    def pair(f):
        return f(a, b)
    return pair
```
    
    
Implement ```car``` and ```cdr```.


Kai's Solution

```python3
def car(pair):
    def return_a(a, b):
        return a
    return pair(return_a)

def cdr(pair):
    def return_b(a, b):
        return b
    return pair(return_b)
```
