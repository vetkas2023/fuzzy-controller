# fuzzy-controller

Вот тут будет проект, надеюсь

1) картинка первого графика и код

![image](https://github.com/vetkas2023/fuzzy-controller/assets/143996115/293f0db5-80b9-477c-895d-eda0b3b8b55b)

```python
import matplotlib.pyplot as plt
import numpy as np



lst_y = []
lst_x = []
for x in np.arange(-4, 4, 0.1):
    if x < -2 or x > 2:
        y = 0
    elif x <= 2 and x >= -2:
        y = 1
    lst_x.append(x)
    lst_y.append(y)


fig, ax = plt.subplots()
ax.plot(lst_x, lst_y)
plt.show()
```

2) картинка второго графика и код

![image](https://github.com/vetkas2023/fuzzy-controller/assets/143996115/b2522944-a906-4a31-8317-2ffb0932097a)
```python
import matplotlib.pyplot as plt
import numpy as np



lst_y = []
lst_x = []
for x in np.arange(-4, 4, 0.1):
    if x < -2 or x > 2:
        y = 0
    elif x <= 1 and x >= -1:
        y = 1
    elif x >= -2 and x < 1:
        y += 0.1
    elif x > 1 and x <= 2:
        y -= 0.1
    lst_x.append(x)
    lst_y.append(y)


fig, ax = plt.subplots()
ax.plot(lst_x, lst_y)
plt.show()
```
3) переделали в функцию первый график
   ![image](https://github.com/vetkas2023/fuzzy-controller/assets/143996115/4385dac4-8861-4ee0-9a93-427fbf578c22)
```python
import matplotlib.pyplot as plt
import numpy as np


def  func1(x, a, b):
    f = 0
    if a <= x <= b:
        f = 1
    return f


lst_x = np.arange(-4, 4, 0.1)
lst_y = []
for x in lst_x:
    y = func1(x, 2, 3)
    lst_y.append(y)

fig, ax = plt.subplots()
ax.plot(lst_x, lst_y)
plt.show()
```

4)переделали в функцию второй график
![image](https://github.com/vetkas2023/fuzzy-controller/assets/143996115/d0875600-5c0f-4e27-9151-334ff04bc343)
```python
import matplotlib.pyplot as plt
import numpy as np


def func(x, a, b, c, d):
    f = 0
    if x < a:
        f = 0
    elif x > d:
        f = 0
    elif a <= x < b:
        f = (x - a) / (b - a)
    elif b <= x <= c:
        f = 1
    elif c < x <= d:
        f = (d - x) / (d - c)
    return f


lst_x = np.arange(-4, 4, 0.1)
lst_y = []
for x in lst_x:
    y = func(x, 0, 1, 2, 3)
    lst_y.append(y)

fig, ax = plt.subplots()
ax.plot(lst_x, lst_y)
plt.show()
```
5)во второй фунции мы сделали два графика двух нечётких чисел и нашли их максимум

![image](https://github.com/vetkas2023/fuzzy-controller/assets/143996115/b73064ed-2b67-4aea-9c84-42afa32bbdd7)
```python
import matplotlib.pyplot as plt
import numpy as np


def func(x, lst):
    a, b, c, d = lst
    f = 0
    if x < a:
        f = 0
    elif x > d:
        f = 0
    elif a <= x < b:
        f = (x - a) / (b - a)
    elif b <= x <= c:
        f = 1
    elif c < x <= d:
        f = (d - x) / (d - c)
    return f


def fmax(x, lst, lst2):
    f1 = func(x, lst)
    f2 = func(x, lst2)
    return max(f1, f2)


lst_x = np.arange(-4, 4, 0.1)
lst_y = []
for x in lst_x:
    y = fmax(x, [-3, -2, -1, 0], [-1, 0, 1, 2])
    lst_y.append(y)

fig, ax = plt.subplots()
ax.plot(lst_x, lst_y)
plt.show()
```
6)во второй фунции мы сделали два графика двух нечётких чисел и нашли их минимум


![image](https://github.com/vetkas2023/fuzzy-controller/assets/143996115/1ef10482-7cc0-46e1-b947-346ebdeb0558)
```python
import matplotlib.pyplot as plt
import numpy as np


def func(x, lst):
    a, b, c, d = lst
    f = 0
    if x < a:
        f = 0
    elif x > d:
        f = 0
    elif a <= x < b:
        f = (x - a) / (b - a)
    elif b <= x <= c:
        f = 1
    elif c < x <= d:
        f = (d - x) / (d - c)
    return f


def fmin(x, lst, lst2):
    f1 = func(x, lst)
    f2 = func(x, lst2)
    return min(f1, f2)


lst_x = np.arange(-4, 4, 0.1)
lst_y = []
for x in lst_x:
    y = fmin(x, [-3, -2, -1, 0], [-1, 0, 1, 2])
    lst_y.append(y)

fig, ax = plt.subplots()
ax.plot(lst_x, lst_y)
plt.show()
```

 7)Найдём центр тяжести трапиевидного числа
 ![image](https://github.com/vetkas2023/fuzzy-controller/assets/143996115/25659a09-4a93-4e36-a1de-6be2b9d6f19f)
 ```python
    elif b <= x <= c:
        f = 1
    elif c < x <= d:
        f = (d - x) / (d - c)
    return f


def fcentr(x, lst):
    a, b, c, d = lst
    f1 = func(x, lst)
    g = (a ** 2 + b ** 2 - c ** 2 - d ** 2 + b * a - c * d) / (a + b - c - d) * 1 / 3
    return g


lst_x = np.arange(-4, 4, 0.1)
lst_y = []
for x in lst_x:
    y = fcentr(x, [-3, -2, -1, 0])
    lst_y.append(y)

fig, ax = plt.subplots()
ax.plot(lst_x, lst_y)
plt.show()
```
