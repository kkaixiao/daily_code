**Question: return index of an item in an array, if not found, return -1**


** Solution using recursion **
```python3
def binary_search_rec(arr, item, left = 0, right = 1):
    if right < left:
        return -1
    
    middle = left + (right - left)//2
    print('middle index:' + str(middle))
    
    if arr[middle] == item:
        return middle
    elif arr[middle] > item:
        return binary_search(arr, item, left, middle-1)
    else:
        return binary_search(arr, item, middle+1, right)

if __name__ == '__main__':
    lst = [2, 5, 3, 8, 22, 17, 30, 1, 4, 100, 35, 72, 9, 6]
    lst.sort()
    print(lst[binary_search(sorted(lst), 30, 0, len(lst)-1)])
```
  
 ** Solution using iteration **
 
 ```python3
 def binary_search_ite(arr, item):
    sorted_arr = sorted(arr)
    left, right = 0, len(arr)-1
    middle = len(arr)//2
    found = False
    while right > left:
        if sorted_arr[middle] == item:
            found = True
            break
        elif sorted_arr[middle] > item:
            right = middle -1
        elif sorted_arr[middle] < item:
            left = middle + 1
            
        middle = (left + right) // 2
        print(left, middle, right)
    if found:
        return arr.index(sorted_arr[middle])
    else:
        return -1
        
if __name__ == '__main__':
    lst = [2, 5, 3, 8, 22, 17, 30, 1, 4, 100, 35, 72, 9, 6]
    print(binary_search_ite(sorted(lst), 30))
```

 ** We can use the while .. else statement to avoid the use of 'found' variable **
 ```ptyhon3
 def binary_search_ite2(arr, item):
    sorted_arr = sorted(arr)
    left, right = 0, len(arr)-1
    middle = len(arr)//2
    while right > left:
        if sorted_arr[middle] == item:
            return arr.index(sorted_arr[middle])
        elif sorted_arr[middle] > item:
            right = middle -1
        elif sorted_arr[middle] < item:
            left = middle + 1
            
        middle = (left + right) // 2
    
    else:
        return -1
        
 if __name__ == '__main__':
    lst = [2, 5, 3, 8, 22, 17, 30, 1, 4, 100, 35, 72, 9, 6]
    print(binary_search_ite2(sorted(lst), 30))
