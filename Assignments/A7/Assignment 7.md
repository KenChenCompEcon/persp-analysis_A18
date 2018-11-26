
### Q1

#### Problem1:

Define the smallest_factor function


```python
def smallest_factor(n):
    """Return the smallest prime factor of the positive integer n."""
    if n == 1: return 1
    for i in range(2, int(n**.5)):
        if n % i == 0: return i
    return n
```

Define the unittest functions


```python
from smallest_factor import smallest_factor

def test_one():    
    assert smallest_factor(1) == 1, "failed on 1"
def test_small_prime():
    assert smallest_factor(6) == 2, "failed on 6"
def test_big_prime():
    assert smallest_factor(11) == 11, "failed on 11"
```


```python
py.test
```

Corrected function


```python
def smallest_factor_corrected(n):
    """Return the smallest prime factor of the positive integer n."""
    if n == 1: return 1
    for i in range(2, int(n**.5)+1):
        if n % i == 0: return i
    return n
```

#### Problem2:

check the coverage for problem 1

<img src="https://github.com/KenChenCompEcon/persp-analysis_A18/blob/master/Assignments/A7/unittest_coverage.png?raw=true" width="600" height="300" />

As reported, my unittests for problem1 are already comprehensive.


```python
def month_length(month, leap_year=False):
    """Return the number of days in the given month."""
    if month in {"September", "April", "June", "November"}:
        return 30
    elif month in {"January", "March", "May", "July", "August", "October", "December"}:
        return 31
    if month == "February":
        if not leap_year:
            return 28
        else:
            return 29
    else:
        return None
```

Unittests


```python
from month_length import month_length

def test_30days():
    assert month_length('June')==30, "failed on June"

def test_31days():
    assert month_length('October')==31, "failed on October"

def test_leapFeb():
    assert month_length('February', leap_year=True)==29, "failed on February in leap years"

def test_nonleapFeb():
    assert month_length('February', leap_year=False)==28, "failed on February in non-leap years"

def test_valueError():
    assert month_length('Homework')==None, "failed on wrong inputs"
```

As reported, these tests have a comprehensive coverage

<img src="https://github.com/KenChenCompEcon/persp-analysis_A18/blob/master/Assignments/A7/unittest_1.2.png?raw=true" 
width="600" height="300" />

#### Problem3


```python
def operate(a, b, oper):
    """Apply an arithmetic operation to a and b."""
    if type(oper) is not str:
        raise TypeError("oper must be a string")
    elif oper == '+':
        return a + b
    elif oper == '-':
        return a - b
    elif oper == '*':
        return a * b
    elif oper == '/':
        if b == 0:
            raise ZeroDivisionError("division by zero is undefined")
        return a / b
    raise ValueError("oper must be one of '+', '/', '-', or '*'")
```

unittests


```python
from operate import operate
import pytest

def test_str():
    with pytest.raises(TypeError) as e:
        operate(1,2,x)
        print(e)
```

As reported, all methods have been tested, including the exceptions.

<img src="https://github.com/KenChenCompEcon/persp-analysis_A18/blob/master/Assignments/A7/unittest_1.3.png?raw=true" 
width="600" height="300" />
