# Forward-forward-NLP

## Different Dataset(small) experiments

Train data: 1000 

Test data: 600

```python
# embedding method
EMBD = 'sbert' # choose from 'GloVe' or 'sbert'
# Corruption: if not then concatnate
INSERT = False 
# goodness function
def goodness(X):
  return goodness_power(X,4.3)
```

| DATASET            | FFA Acc | BP Acc |
| ------------------ | ------- | ------ |
| AG_NEWS            | 94.11%  | 27.67% |
| AmazonReviewFull   | 74.00%  | 19.67% |
| DBpedia            | 100%    | 100%   |
| IMDb               | 100%    | 100%   |
| YahooAnswers       | 72.84%  | 22.3%  |
| YelpReviewFull     | 74.21%  | 30.83% |
| YelpReviewPolarity | 100%    | 74.83% |



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
| sbert(384) | 89.09%    | 89.09%   | 98.51%   | 91.34%  |



### Corruption - Acc

**Setting:**

- Data set: AG News

- Embedding: **sbert**

- Goodness: Sum of square

- Negative Samples: positive data + random label

**Results:**

| Corruption  | FFA-train | FFA-test | BP-train | BP-test |
| ----------- | --------- | -------- | -------- | ------- |
| Insert      | 89.09%    | 89.09%   | 98.51%   | 91.34%  |
| Concatenate | 89.16%    | 89.16%   | /        | /       |



### Goodness - Acc

**Setting:**

- Data set: AG News
- Corruption: concatenate
- Embedding: sbert
- Negative Samples: positive data + random label

**Results:**

| BP-train | BP-test |
| :------: | :-----: |
|  98.51%  | 91.34%  |



| Goodness Function              | FFA-train   | FFA-test    | Train_loss                                                   |
| ------------------------------ | ----------- | ----------- | ------------------------------------------------------------ |
| sqrt                           | 24.97%      | 24.97%      | <img src="../../Library/Application Support/typora-user-images/image-20230416180808372.png" alt="image-20230416180808372" style="zoom:50%;" /> |
| Absolute                       | 25.03%      | 25.03%      | <img src="../../Library/Application Support/typora-user-images/image-20230416182938629.png" alt="image-20230416182938629" style="zoom:50%;" /> |
| Power(2)                       | 89.23%      | 89.23%      | <img src="../../Library/Application Support/typora-user-images/image-20230416152310710.png" alt="image-20230416152310710" style="zoom:50%;" /> |
| Power(3)                       | 91.99%      | 91.99%      | <img src="../../Library/Application Support/typora-user-images/image-20230416155254864.png" alt="image-20230416155254864" style="zoom:50%;" /> |
| Power(4)                       | 93.23%      | 93.23%      | <img src="../../Library/Application Support/typora-user-images/image-20230416160805970.png" alt="image-20230416160805970" style="zoom:50%;" /> |
| Power(4.2)                     | 93.32%      | 93.32%      | <img src="../../Library/Application Support/typora-user-images/image-20230416191138833.png" alt="image-20230416191138833" style="zoom:50%;" /> |
| Power(5)/Power(4.5)/Power(4.3) | 24.99%(nan) | 24.99%(nan) | <img src="../../Library/Application Support/typora-user-images/image-20230416164222144.png" alt="image-20230416164222144" style="zoom:50%;" /> |
| Power(6)                       | 24.99%(nan) | 24.99%(nan) | <img src="../../Library/Application Support/typora-user-images/image-20230416174026154.png" alt="image-20230416174026154" style="zoom:50%;" /> |
|                                |             |             |                                                              |



