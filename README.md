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

dataset = loader.load()

# Load query, document features, relevance ratings, and number of documents
query_id, x, y, n = dataset[0]
```
