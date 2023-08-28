# LTR Datasets

## Installation

```
pip install ltr-datasets
```

## Example

```Python
from ltr_datasets.datasets import MSLR10K
from ltr_datasets.transformations import (
    Log1pNormalize,
    StratifiedTruncate,
)

loader = MSLR10K(
    fold=1,
    split="train",
    transform=[
        Log1pNormalize(),
        StratifiedTruncate(max_length=10, random_state=42),
    ],
)

# Load PyTorch dataset, which is cached by default after the first load.
# To overwrite the cached dataset, e.g., after changing transformations, use .load(force_reload=True)
dataset = loader.load()

# Each entry is a search query with id, document features, relevance ratings, and number of documents.
query_id, x, y, n = dataset[0]
```
