This problem was asked by Uber.

Given an array of integers, return a new array such that each element at index i of the new array is the product of all the numbers in the original array except the one at i.

For example, if our input was [1, 2, 3, 4, 5], the expected output would be [120, 60, 40, 30, 24]. If our input was [3, 2, 1], the expected output would be [2, 3, 6].

Follow-up: what if you can't use division?

Kai's solutions:
```python3
# solution with the use of division
def product_all_except_self(l):
    res = []
    all_prod = 1
    for num in l:
        all_prod *= num
    for n in l:
        res.append(int(all_prod/n))
    return res
    
    
# solution with the use of division
import numpy as np

def product_all_except_self_withou_division(l):
    res = []
    for i, num in enumerate(l):
        left_product = np.prod(l[:i])
        if left_product == 0 or len(l[:i]) == 0:
            left_product = 1
        right_product = np.prod(l[i+1:])
        if right_product == 0 or len(l[i+1:]) == 0:
            right_product = 1
        res.append(int(left_product*right_product))
    return res
```
        
