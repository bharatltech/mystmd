```{code-cell} python
# This is a Python code cell that will be executable
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.figure(figsize=(8, 4))
plt.plot(x, y)
plt.title("Sine Wave")
plt.show()
```
