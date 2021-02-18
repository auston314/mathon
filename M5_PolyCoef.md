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

# Math 5 - Polynomial Coefficients
To also use binary search to find iteration number and exponent to solve mathematical equation. (Not generic).

```python
def dectobi(dec_number): 
    bin_array = []
    #array.insert(index, value)
    for i in range(32):
        if dec_number == 0:
            break
        digit = dec_number % 2
        dec_number = int(dec_number/2)
        bin_array.insert(0, digit)
        #print(digit)
    return bin_array
    
dectobi(14205)  
```

```python
def getterm(padded_bin,con):
    n_digits = len(padded_bin)
    power_x = 0
    coeffi = 1
    for i in range(n_digits):
        if padded_bin[i] == 0:
            power_x += 1
        else:
            coeffi *= con[i]
    return coeffi,power_x

```

```python
con = [1,3,3,2,1]
def polynomial_coefficients(con):
    zeros = [0 for i in range(len(con))]
    poly_coef = [0 for i in range(len(con)+1)]
    for i in range(2**len(con)):
        y = dectobi(i)
        n_digits = len(y)
        padded_bin = zeros[:len(con)-n_digits] + y
        print(padded_bin)
        coeffi,power_x = getterm(padded_bin,con)
        poly_coef[power_x] += coeffi
    return poly_coef 

polynomial_coefficients(con)
```

```python

```

```python
# procedure is to find how many ones, and to take the remaining 0 slots to multipy the coefficients. 
#assign each column with a coefficient.
\
def count_add(coeffi,power_x):
    
```

```python
import math
def mfunc(x):
    y = 1.035**x + 1.07**x
    print(y)
    return y
def binarysearch(lower_bound,upper_bound,target_value):
    lower_value = mfunc(lower_bound)
    upper_value = mfunc(upper_bound)
    #middle_point = (upper_bound+lower_bound)/2
    h1 = target_value-lower_value
    h2 = upper_value-target_value
    middle_point = (lower_bound*h2+upper_bound*h1)/(h1+h2)
    middle_value = mfunc(middle_point)
    if middle_value <= target_value:
        new_upper_bound = upper_bound
        new_lower_bound = middle_point
    else:
        new_upper_bound = middle_point
        new_lower_bound = lower_bound
    return new_lower_bound,new_upper_bound,middle_value

target_value = 6
upper_bound = 30
lower_bound = 17

lower_bound,upper_bound,approximate_value = binarysearch(lower_bound,upper_bound,target_value)
print(lower_bound,upper_bound,approximate_value)
  
for i in range(40):
    eps = 0.000000000001
    lower_bound,upper_bound,approximate_value = binarysearch(lower_bound,upper_bound,target_value)
    print("Iteration Number: ",i,lower_bound,upper_bound,approximate_value)
    if math.fabs(approximate_value - target_value) <= eps:
        break
```

```python

```
