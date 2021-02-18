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

# Math 3 - Newton Iteration
Use Newton's Iteration to solve an equation of any smooth and continuous function. 

```python
import math
def derivative(x):
    return 2*x
def newton_update(x0,h0,f_prime_x):
    x1 = x0 - h0/f_prime_x
    return x1

print(math.sqrt(2))
```

```python
#solve x^2-2 = 0 
x0 = 1.4
h0 = x0**2-2
f_prime_x0 = derivative(x0)
x1 = newton_update(x0,h0,f_prime_x0)
h1 = x1**2-2
f_prime_x1 = derivative(x1)
x2 = newton_update(x1,h1,f_prime_x1)
h2 = x2**2-2
f_prime_x2 = derivative(x2)
x3 = newton_update(x2,h2,f_prime_x2)
print(x1,x2,x3)
```

```python
def newton_iteration(x0,max_it = 5):
    eps = 0.000000000000001
    for i in range(max_it):
        h0 = x0**2-2
        if math.fabs(h0) < eps:
            break
        f_prime_x0 = derivative(x0)
        x0 = newtonit(x0,h0,f_prime_x0)
        print(x0)
    
```

```python
newton_iteration(5,7)
```

```python
def derivative2(x):
    return 4*x+6
def fx(x):
    return 2*x**2+6*x-5
def newton_iteration(x0,max_it = 5):
    eps = 0.000000000000001
    for i in range(max_it):
        h0 = fx(x0)
        if math.fabs(h0) < eps:
            break
        f_prime_x0 = derivative2(x0)
        x0 = newtonit(x0,h0,f_prime_x0)
        print(x0)
```

```python
x1 = (-3+math.sqrt(19))/2
x2 = (-3-math.sqrt(19))/2
print("Solution 1",x1)
print("Solution 2",x2)
newton_iteration(-3.5,7)
newton_iteration(5,7)
```

```python
import math
import matplotlib.pyplot as plt
import numpy as np
%matplotlib inline

fig, ax = plt.subplots(figsize=(10,10))
x = np.linspace(-3.5,1.5,100)
y = x**3+3*x**2-x-3
plt.plot(x,y,'r')
plt.grid(alpha=100,linestyle='--')
ax.set(xlabel='x-axis', ylabel='y-axis',title = "plotting equations")
```

```python
def newton_iteration2(x0,max_it = 5):
    eps = 0.000000000000001
    for i in range(max_it):
        h0 = x0**2-2
        if math.fabs(h0) < eps:
            break
        f_prime_x0 = derivative(x0)
        x0 = newtonit2(x0,h0,f_prime_x0)
        print(x0)
```

```python

def derivative3(x):
    return 3*x**2+6*x-1
def fx2(x):
    return x**3+3*x**2-x-3
def newton_iteration2(x0,max_it = 5):
    eps = 0.000000000000001
    for i in range(max_it):
        h0 = fx2(x0)
        if math.fabs(h0) < eps:
            break
        f_prime_x0 = derivative3(x0)
        x0 = newton_update(x0,h0,f_prime_x0)
        print("iteration ",i+1,"results ",x0)
    return x0
```

```python
x1 = 2
x2 = -4
x3 = -0.5
print("Solution 1",x1)
print("Solution 2",x2)
print("Solution 3",x3)
newton_iteration2(x1,7)
newton_iteration2(x2,7)
newton_iteration2(x3,5)
```

```python
def peak_checker(fx2,x0,x1,x2):
    y0 = fx2(x0)
    y1 = fx2(x1)
    y2 = fx2(x2)
    #lets label top peak as 1, and valley point as -1 and all others as 0. 
    if y1 > y0 and y1 > y2:
        return 1
    if y1 < y0 and y1 < y2:
        return -1
    return 0
def peak_finder(fx2,start_x = -5,end_x = 5,n_grids= 100):
    step_size = (end_x-start_x)/n_grids
    for i in range(n_grids):
        x0 = start_x + i*step_size
        x1 = x0 + step_size
        x2 = x1 + step_size
        if peak_checker(fx2,x0,x1,x2) == 1:
            y1 = fx2(x1)
            print("Peak Found at ",x1,y1)
            
        if peak_checker(fx2,x0,x1,x2) == -1:
            y2 = fx2(x1)
            print("Valley Found at ",x1,y2)

peak_finder(fx2,n_grids = 1000000)

```

```python
print("solution 1 ",(-1+math.sqrt(12)/3))
print("solution 2 ",(-1-math.sqrt(12)/3))
```

```python

```
