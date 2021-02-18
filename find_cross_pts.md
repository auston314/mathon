---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.2'
      jupytext_version: 1.5.2
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Find Cross Points
To solve for two systems of equations.

```python
def linear_solver(abc1,abc2):
    """
    this solves a set of linear equations
    abc1 contains three parameter for first equation, abc2 contains three parameters for second equation 
    """
    A = abc1[0]
    B = abc1[1]
    C = abc1[2]
    
    D = abc2[0]
    E = abc2[1]
    F = abc2[2]
    #print(A*E,D*B)
    #print(B*F-C*E)
    #print(D*C-F*A)
    if (A*E - D*B == 0 and B*F - C*E == 0):
        print("Two Lines are equal!")
        return "Equal","Line"
    
    if (A*E - D*B == 0 and B*F - C*E != 0):
        print("No Solution!")
        return "No","Solution"
    
    x = (B*F - C*E)/(A*E - D*B)
    y = (D*C - F*A)/(A*E - D*B)
    
    return x,y

abc1 = [1,2,-3]
abc2 = [4,-5,6]
linear_solver(abc1,abc2)
    
```

```python
def find_linear_equation(p1, p2):
    """
    give two points (p1, p2), find the linear equation
    for the line passing through the two points. ax + by + c = 0
    
    """
    #case 0 is if the two points are overlapping. check coordinates for matching x and y. 
    if p1[0] == p2[0] and p1[1] == p2[1]:
        #in this case, return as error
        print("You dummy! The points are the same! Line is undetermined!")
        return None
    #case 1 is if the line is vertical. check coordinates for matching x. 
    if p1[0] == p2[0]:
        #in this case, a = 1, b = 0, and c needs to be found. 
        c = -p1[0]
        a = 1
        b = 0
        return a,b,c
    #case 2 is if the line is horizontal. check coordinates for matching y. 
    if p1[1] == p2[1]:
        #in this case, a = 0, b = 1, c = needs to be found. 
        c = -p1[1]
        a = 0
        b = 1
        return a,b,c
    #case 3 is if the line is general. The equation can always be written as y = ax + b
    #first compute the slope, which is delta y / delta x.
    a = (p2[1]-p1[1])/(p2[0]-p1[0])
    c = p1[1]-a*p1[0]
    b = -1
    return a,b,c
    
find_linear_equation((0,0),(0,0))  
```

```python
line_1 = [(1,1),(2,2)]
line_2 = [(1,2),(2,1)]
line_3 = [(1,1),(2,2)]
line_4 = [(2,1),(3,0)]
line_5 = [(1,1),(2,2)]
line_6 = [(2,1),(3,2)]

```

```python
def point_on_segment(p1,p2,x,y):
    #if x is between p1[0] and p2[0] and y is between p1[1] and p2[1]
    #use max and min to get the boundary of the two points.
    max_x = max(p1[0],p2[0])
    min_x = min(p1[0],p2[0])
    max_y = max(p1[1],p2[1])
    min_y = min(p1[1],p2[1])
    if x >= min_x and x <= max_x and y >= min_y and y <= max_y:
        return True
    else:
        return False
    
```

```python
point_on_segment((3,3),(1,2.5),2.5,2.5)
```

```python
line
```

```python
# step 1: find linear equations for the line segments.
# step 2: find the cross point of the two linear equations from step 1.
#         case A: find the cross point.
#.        case B: there is no cross point of linear equation
# step 3: for case B of step 2,  there will be no cross point for the line segments.
# for case B of step 2, there are still two subcases.
#.      case B1 = the cross point is not in the line segment, and the two line segments are not crossing
#.      case B2 = the two line segments cross each other.

def findcrosspoint (line_1,line_2):
    p1 = line_1[0]
    p2 = line_1[1]
    a,b,c = find_linear_equation(p1,p2)
    p1 = line_2[0]
    p2 = line_2[1]
    d,e,f = find_linear_equation(p1,p2)
    abc1 = [a,b,c]
    abc2 = [d,e,f]
    x,y = linear_solver(abc1,abc2)
    if x == "Equal":
        print("Overlapping!")
        cross = True
        return cross
    if x == "No":
        print("No Crossing")
        cross = False
        return cross
    #now, lets check the cross point.
    if point_on_segment(line_1[0],line_1[1],x,y) and point_on_segment(line_2[0],line_2[1],x,y):
        cross = True
    else:
        cross = False 
    return cross
findcrosspoint(line_1,line_2)
```

```python
max(1,2,2,5,7,2,5)
```

```python

```

```python
points = [(1,-1),(2,-1),(3,1),(2,2),(0,1)]
points2 = [(0,0),(1,1),(3,-1),(3,1),(1,-1)]

```

```python
def findedgepairs(n_points):
    edge_pairs = []
    for  i in range(n_points):
        for j in range(i+2,n_points):
            if i == 0 and j == n_points-1:
                continue
            #print (i,j)
            edge_pairs.append((i,j))
    return edge_pairs
findedgepairs(5)
```

```python
import math
import matplotlib.pyplot as plt
%matplotlib inline
```

```python
def shoelacetheorm (vertice):
    vertice.append(vertice[0])
    np = len(vertice)
    s = 0
    for i in range(np-1):
        p1 = vertice[i]
        p2 = vertice[i+1]
        s += p1[0]*p2[1] - p2[0]*p1[1]
        
    s = s/2 
    if s < 0:
        s = -s
    return s
    

vtx1 = []
vtx1.append([1,1])
vtx1.append([1,7])
vtx1.append([2,1])

vtx2 = [[1,1],[-1,1],[-1,-1],[1,-1]]

print("Now, test my code!")
time.sleep(2)
print('Area of polygon 1', shoelacetheorm(vtx1))
print('Area of polygon 2', shoelacetheorm(vtx2))



```

```python
def checkcross(points):
    #step 1: find all pairs of edges that need to be checked for cross. 
    #step 2: loop for all those pairs and check for cross points.
    #step 3: if any of those pairs have cross points, return True, else False. 
    edgepairs = findedgepairs(len(points))
    for epair in edgepairs:
        edge_a = epair[0]
        edge_b = epair[1]
        a1 = edge_a
        a2 = a1+1
        b1 = edge_b
        b2 = b1+1
        if a2 >= len(points):
            a2 = 0
        if b2 >= len(points):
            b2 = 0
        line1 = (points[a1],points[a2])
        line2 = (points[b1],points[b2])
        if findcrosspoint(line1,line2):
            print("error: cannot process due to crosspoint.")
            return True
    return False

checkcross(points)
```

```python

```

```python
import math
import matplotlib.pyplot as plt
%matplotlib inline

def plot_rectangle (x0, y0, length , width ,ax, color):
    #def plot_box (width = 4, height= 2):
    x = [x0,x0,x0+ length, x0 + length, x0]
    y = [y0, y0 + width,y0 +width ,y0,y0]
    ax.plot(x, y, color)
    
fig, ax = plt.subplots(figsize=(4, 4))
ax.set(xlabel='X', ylabel='Y',title = "a rectangle")

def plot_polygon(points,ax,color):
    #creates a list of x and creates a list of y from points.
    np = len(points)
    x = []
    y = []
    for i in range(np):
        x0 = points[i][0]
        y0 = points[i][1]
        x.append(x0)
        y.append(y0)
        
    x0 = points[0][0]
    y0 = points[0][1]
    x.append(x0)
    y.append(y0)
    ax.plot(x,y,color)
plot_rectangle(-1,-3,6,6,ax,'b')
plot_polygon(points2,ax,'b')
plot_polygon(points,ax,'r')
```

```python
def areabyshoelace(points):
    fig, ax = plt.subplots(figsize=(4, 4))
    plot_rectangle(-1,-3,6,6,ax,'b')
    plot_polygon(points,ax,'g')
    c = checkcross(points)
    if c:
        print("Hi dummy.")
    else:
        print("Area of polygon is",shoelacetheorm(points))
areabyshoelace(points2)
areabyshoelace(points)  
```

```python

```

```python

```
