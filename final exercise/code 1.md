```python
import matplotlib.pyplot as plt
import random

position = 0
walk = [position]
steps = 2000
for i in range(steps):
    step = 1 if random.randint(0, 1) else -1
    position += step
    walk.append(position)

fig = plt.figure()
ax = fig.add_subplot(111)
ax.plot(walk)
plt.show()
