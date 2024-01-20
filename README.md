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


def  func(x, a, b):
    f = 0
    if a <= x <= b:
        f = 1
    return f


lst_x = np.arange(-4, 4, 0.1)
lst_y = []
for x in lst_x:
    y = func(x, 2, 3)
    lst_y.append(y)

fig, ax = plt.subplots()
ax.plot(lst_x, lst_y)
plt.show()
```
