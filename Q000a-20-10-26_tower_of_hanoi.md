** Question: Tower of Hanoi ** (https://en.wikipedia.org/wiki/Tower_of_Hanoi)


**Solution:**

```python3
def hanoi_tower(n, rod_from, rod_middle, rod_to):
    if n == 1: # when n-1 plates are in the final rod
        print('Plate 1 from {} to {}'.format(rod_from, rod_to))
        return
        
    # moving n-1 plates off the largest one to be able to move
    hanoi_tower(n-1, rod_from, rod_to, rod_middle)
    
    # moving the actual largest one
    print('Plate {} from {} to {}'.format(n, rod_from, rod_to))
    
    # placing n-1 plates on top of the largest one
    hanoi_tower(n-1, rod_middle, rod_from, rod_to)
    
if __name__ == '__main__':
    hanoi_tower(4, 'a', 'b', 'c')

```
