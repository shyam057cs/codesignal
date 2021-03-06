# Problem
Below we will define an n-interesting polygon. Your task is to find the area of a polygon for a given n.

A 1-interesting polygon is just a square with a side of length 1. An n-interesting polygon is obtained by taking the n - 1-interesting polygon and appending 1-interesting polygons to its rim, side by side. You can see the 1-, 2-, 3- and 4-interesting polygons in the picture below.
![shapeImage](https://github.com/kah-ve/codesignal/blob/master/Arcade/shapeArea/area.png)

For n = 2, the output should be shapeArea(n) = 5 

# Solution
```python
def shapeArea(n):
    if n == 0:
        return 0
    area = 1
    for i in range(n):
        area += 4*i
    return area
```
