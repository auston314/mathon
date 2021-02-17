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

# Block Rotation Math Problem 
## Probability of color change post-rotation. 

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
    
dectobi(11)  
```

```python
def daddy_dec2bin(dec_number):
    max_length = 16
    bin_array = [0 for i in range(max_length)]
    for i in range(max_length):
        bin_array[-i-1] = dec_number%2
        dec_number = int(dec_number/2)
    return bin_array

total = 2 << 15
for i in range(total):
    print(daddy_dec2bin(i))
```

```python
def dundy_dec2bin(dec_number):
    max_length = 16
    binary_array = []
    for i in range(max_length):
        digit = (dec_number % 2)
        dec_number = int(dec_number/2)
        binary_array.insert(0,digit)
    return binary_array

x = dundy_dec2bin(256)
#mystring = "".join(x)
#print(mystring)
```

```python
rotate_map = {0:1,1:2,2:3,3:0,4:7,5:8,6:9,7:10,8:11,9:12,10:13,11:14,12:15,13:4,14:5,15:6}
def rotate_digits(input_digits):
    input_length = len(input_digits)
    print(input_digits,input_length)
    output_digits = [0 for i in range(input_length)]
    for i in range(input_length):
        output_digits[rotate_map[i]] = input_digits[i]
        #output_digits[i-2] = input_digits[i]
    return output_digits
decimal_number = 
x = dundy_dec2bin(decimal_number)
s = rotate_digits(x)
print(s)
```

```python

def checkcolor(input_digits):
    rotatedigits = rotate_digits(input_digits)
    blackness = 1
    input_length = len(input_digits)
    #now, lets check if any bucket is white
    #if yes, return 0, other wise, return 1
    for i in range(input_length):
        if input_digits[i] < 1 and rotatedigits[i] < 1:
            return(0)
    return(1)
#checkcolor(input_digits)
```

```python
number_of_patterns = 2 << 15
black_counter = 0
for i in range(number_of_patterns):
    input_digits = daddy_dec2bin(i)
    checkcolor(input_digits)
    b = checkcolor(input_digits)
    if b == 1:
        black_counter += 1
print(black_counter)
```

```python

```
