# Forward-forward-NLP

## Background

**Data Set**: AG News

- Training: 120,000 news articles
- Testing: 7,600 news articles

**Task**: Text Classification

- 4 classes (“World”, “Sports”, “Business”, “Sci/Tech”)

**Embedding**: GloVe(name='840B', dim=300)

## Experiments

**Common Treatment:**

- take *average* of each word embeddings in the article
- put embeddings into 4 layer neural networks
- train-valid ratio: 95:5 



**Baseline Results:**

Test Accuracy : 0.9180

Classification Report :               

|					|precision |   recall|  f1-score |  support|        
| ---  | ---  | ---  | ---  | ---  |
|World   |    0.93    |  0.91   |   0.92    |  1900      |
|Sports   |    0.98   |   0.97     | 0.97  |    1900    |
|Business   |    0.86  |    0.90    |  0.88  |    1900    |
|Sci/Tech    |   0.91   |   0.89  |    0.90  |    1900     |
|accuracy| | |                         0.92    |  7600  | 
|macro avg    |   0.92    |  0.92    |  0.92   |   7600 |
|weighted avg  |     0.92  |    0.92   |   0.92   |   7600  |

Confusion Matrix :  

[[1736   29   92   43] 

[  31 1837   24    8]

 [  54    8 1717  121]

 [  46   10  157 1687]]



<img src="image/baseline_conf_matrix.png" alt="baseline_conf_matrix" style="zoom:60%;" />