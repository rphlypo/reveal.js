## Part X
### Data in python

```python
import numpy as np
from scipy.stats import gaussian_kde

X = np.random.uniform(size=(100, 100))
s = X.sum(axis=0)
gaussian_kde(s)
```
