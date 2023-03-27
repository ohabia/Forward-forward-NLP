# Forward-forward-NLP

## Background

**Task**: Text Classification

**Data Set**: AG News

- Training: 120,000 news articles
- Testing: 7,600 news articles

- 4 classes (“World”, “Sports”, “Business”, “Sci/Tech”)

**Embedding**: 

- GloVe(name='840B', dim=300)

- sbert:  sentence bert, dim = 384

## Experiments

**Common Treatment:**

- put embeddings into 4-layer neural networks
- train-valid ratio: 95:5 

### Embedding - Acc

**Setting:**

- Data set: AG News

- Corruption: insert

- Goodness: Sum of square

- Negative Samples: positive data + random label

**Results:**

|            | FFA-train | FFA-test | BP-train | BP-test |
| ---------- | --------- | -------- | -------- | ------- |
| GloVe(300) | 88.71%    | 88.71%   | 97.9%    | 91.6%   |
| sbert(384) | 67.94%    | 67.84%   | 93.5%    | 74.5%   |

==FFA: each layer's epoch = 1000, maybe should try sth higher | BP epoch 25==

### Embedding - Acc

**Setting:**

- Data set: AG News

- Embedding: GloVe

- Goodness: Sum of square

- Negative Samples: positive data + random label

**Results:**

| Corruption  | FFA-train | FFA-test | BP-train | BP-test |
| ----------- | --------- | -------- | -------- | ------- |
| Insert      | 88.71%    | 88.71%   | 97.9%    | 91.6%   |
| Concatenate | 89.02%    | 89.02%   | /        | /       |



