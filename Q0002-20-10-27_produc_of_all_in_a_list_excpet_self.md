This problem was asked by **Uber**. Difficulty level: **Hard** (though I don't think so)

Given an array of integers, return a new array such that each element at index i of the new array is the product of all the numbers in the original array except the one at i.

For example, if our input was [1, 2, 3, 4, 5], the expected output would be [120, 60, 40, 30, 24]. If our input was [3, 2, 1], the expected output would be [2, 3, 6].

Follow-up: what if you can't use division?

**Kai's solutions:**
```python3
# solution with the use of division

def product_all_except_self(l):
    res = []
    all_prod = 1
    for num in l:
        all_prod *= num
    for n in l:
        if n:
            res.append(int(all_prod/n))
        else:
            res.append(all_prod)
    return res
    
    
# solution with the use of division, we can create a product function to replace numpy's prod method
# but I am just lazy here...

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
**Solution**
This problem would be easy with division: an optimal solution could just find the product of all numbers in the array and then divide by each of the numbers.

Without division, another approach would be to first see that the i<sup>th</sup> element simply needs the product of numbers before i and the product of numbers after i. Then we could multiply those two numbers to get our desired product.

In order to find the product of numbers before i, we can generate a list of prefix products. Specifically, the i<sup>th</sup> element in the list would be a product of all numbers including i. Similarly, we would generate the list of suffix products.

```python3
ef products(nums):
    # Generate prefix products
    prefix_products = []
    for num in nums:
        if prefix_products:
            prefix_products.append(prefix_products[-1] * num)
        else:
            prefix_products.append(num)

    # Generate suffix products
    suffix_products = []
    for num in reversed(nums):
        if suffix_products:
            suffix_products.append(suffix_products[-1] * num)
        else:
            suffix_products.append(num)
    suffix_products = list(reversed(suffix_products))

    # Generate result
    result = []
    for i in range(len(nums)):
        if i == 0:
            result.append(suffix_products[i + 1])
        elif i == len(nums) - 1:
            result.append(prefix_products[i - 1])
        else:
            result.append(prefix_products[i - 1] * suffix_products[i + 1])
    return result
    ```
    This runs in O(N) time and space, since iterating over the input arrays takes O(N) time and creating the prefix and suffix arrays take up O(N) space.
