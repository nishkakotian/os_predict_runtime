# Applying ML techniques to predict execution time of processes

## Introduction 

A good understanding of the execution behavior   of   processes   would  enable   us  to   compose   better scheduling   algorithms.In the shortest   job   first algorithm  prior knowledge  about  how  long  a  process  would  take  to  finish  execution is required.There have been some dynamic methods developed to predict it, but they aren't very accurate.In this project, a  machine learning based approach to  predict  the  runtime  of  processes is explored.The ML algorithms used are Random Forest, MLP(Multilayer  perceptron),  KNN  (K  Nearest  Neighbors),  DecisionTree Regressor and XGBOOST.

## Methodology 

Steps involved :

1. Gathering Data- The traces present in the grid workload dataset  GWA-T-4  AuverGrid  were  used.The  original  dataset has 404177 traces of which many have the value of Runtime as 0.After removing them from the dataset 347612 traces are left, out  of   which   2/3   is used  for training and   1/3   for   testing.   The dataset   consists   of   29   process attributes.

2. Training   ML   models-  Supervised  Machine  learning techniques  namely  KNN, Decision  tree  regressor, Multilayer perceptron(MLP), XGBOOST  and  Random  Forest  were  used to generate ML models using training set.Further, parameter tuning was done to improve results.

3. Evaluation- The generated models were tested for their performance using two metrics namely correlation coefficient and relative absolute error.

## Results

1. Considering only the 9 non-historical attributes

| Model | CC | RAE |
| ----------- | ----------- | ----------- |
| KNN | 0.8542 | 0.2197 |
| Decision Tree | 0.8587 | 0.1711 |
| Random Forest | 0.9030 | 0.1510 |
| **XGBoost** | **0.9047** | **0.1592** |
| MLP |  0.8119 | 0.3417 |

Best results were obtained using following :  
KNN : n = 7  
XGBoost : max-depth = 15  
MLP : hidden layer size = (32,32,32)  
Decision Tree : n_estimators=100  

2. Considering all 16 attributes (historical + non-historical attributes)

| Model | CC | RAE |
| ----------- | ----------- | ----------- |
| KNN | 0.9199 | 0.1112 |
| Decision Tree | 0.9211 | 0.0483 |
| Random Forest | 0.9537 | 0.0443 |
| **XGBoost** | **0.9584** | **0.0656** |
| MLP | 0.9404 | 0.1045 |

Best results were obtained using following :   
KNN : n = 9  
XGBoost : max-depth = 8  
Decision Tree: n_estimators = 200  

## Observation

From   the   results,   it   can   be   observed   that   XGBOOST performs   better   than   the   rest   of   the  algorithms.The best value of  correlation coefficient obtained was  0.9584.  However  the  lowest  value  of  RAE was  obtained  with  Random  Forest.  We can note that the  CPU  burst  time  can  be  predicted  better  when  process attributes  with  historical  information  are  used  rather  than with just non-historical information.


## Acknowledgement
Thanks to   the   AuverGrid   team   and the   owners   of   the   AuverGrid   system   for   providing  the   traces.  
Source : http://gwa.ewi.tudelft.nl/datasets/gwa-t-4-auvergrid


