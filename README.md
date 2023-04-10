# Forward-forward-NLP

# Background

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

- Corruption: **insert**

- Goodness: Sum of square

- Negative Samples: positive data + random label

**Results:**

|            | FFA-train | FFA-test | BP-train | BP-test |
| ---------- | --------- | -------- | -------- | ------- |
| GloVe(300) | 88.71%    | 88.71%   | 97.9%    | 91.6%   |
| sbert(384) | 89.09%    | 89.09%   |          |         |



### Corruption - Acc

**Setting:**

- Data set: AG News

- Embedding: **sbert**

- Goodness: Sum of square

- Negative Samples: positive data + random label

**Results:**

| Corruption  | FFA-train | FFA-test | BP-train | BP-test |
| ----------- | --------- | -------- | -------- | ------- |
| Insert      | 89.09%    | 89.09%   |          |         |
| Concatenate | 89.16%    | 89.16%   | /        | /       |



