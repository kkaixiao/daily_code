```python3
class Square:
    def __init__(self, width, height):
        self._width = width
        self._height = height
    
    @property
    def width(self):
#         print('decorator property ran')
        return self._width
    
    @width.setter
    def width(self, width):
#         print('decorator width.setter ran')
        if width <= 0:
            raise ValueError("Width must positive!")
        else:
            self._width = width
    
    @property
    def height(self):
        return self._height
    
    def __str__(self):
        return 'Retangle, width:{}, height:{}'.format(self.width, self.height)
    
    def __repr__(self):
        return 'Retangle object, width:{}, height:{}'.format(self.width, self.height)
        
r1 = Square(2,3)

r1.width

r1.width = 3

r1.width = -1

str(r1)

r1

print(r1)

```
