# adaptive-nms
Square covering approach for Adaptive 2D Keypoints Non-Maximum Suppression

## Installation

```shell
pip install .
```

## Example

```python
import numpy as np
from anms.ssc import square_covering_adaptive_nms

# random;y generate data
n_kpts = 10000
width, height = 960, 720
kpts_x = np.random.randint(width, size=(n_kpts,))
kpts_y = np.random.randint(height, size=(n_kpts,))
kpts = np.stack([kpts_x, kpts_y], axis=-1)
responses = np.random.random(n_kpts)

kpts_idxs = square_covering_adaptive_nms(
    kpts,  # 2-dimensional array of shape [N, 2]
    responses,  # 1-dimensional array of shape [N,]
    width=1280,  # width of image
    height=835,  # height of image
    target_num_kpts=2048,  # desired number of keypoints left
    indices_only=True,  # if True return indices of selected keypoints, else return selected keypoints
    up_tol=10,  # tolerance for more selected keypoints
    max_num_iter=30,  # maximum number of binary search iterations
)
```
