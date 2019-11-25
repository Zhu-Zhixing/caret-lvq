# caret-lvq

### Description
lvq algorithm has applied to select features subset from caret package(r version).

### Example Data
ScreenID   pregnant  glucose   pressure triceps insulin   mass    pedigree    age     diabetes
1          6         148       72        35       0       33.6    0.627       50      pos
2          1          85       66        29       0       26.6    0.351       31      neg
3          8         183       64         0       0       23.3    0.672       32      pos
4          1          89       66        23      94       28.1    0.167       21      neg
5          0         137       40        35     168       43.1    2.288       33      pos
6          5         116       74         0       0       25.6    0.201       30      neg
7          3          78       50        32      88       31.0    0.248       26      pos
8         10         115        0         0       0       35.3    0.134       29      neg
9          2         197       70        45     543       30.5    0.158       53      pos
10         8         125       96         0       0        0.0    0.232       54      pos
11         4         110       92         0       0       37.6    0.191       30      neg
12        10         168       74         0       0       38.0    0.537       34      pos
13        10         139       80         0       0       27.1    1.441       57      neg
14         1         189       60        23     846       30.1    0.398       59      pos
15         5         166       72        19     175       25.8    0.587       51      pos
16         7         100        0         0       0       30.0    0.484       32      pos
17         0         118       84        47     230       45.8    0.551       31      pos
18         7         107       74         0       0       29.6    0.254       31      pos
19         1         103       30        38      83       43.3    0.183       33      neg
20         1         115       70        30      96       34.6    0.529       32      pos

```

### Usage

```
```

trainControl(method = "boot", number = ifelse(grepl("cv", method), 10, 25),
  repeats = ifelse(grepl("[d_]cv$", method), 1, NA), p = 0.75,
  search = "grid", initialWindow = NULL, horizon = 1,
  fixedWindow = TRUE, skip = 0, verboseIter = FALSE, returnData = TRUE,
  returnResamp = "final", savePredictions = FALSE, classProbs = FALSE,
  summaryFunction = defaultSummary, selectionFunction = "best",
  preProcOptions = list(thresh = 0.95, ICAcomp = 3, k = 5, freqCut = 95/5,
  uniqueCut = 10, cutoff = 0.9), sampling = NULL, index = NULL,
  indexOut = NULL, indexFinal = NULL, timingSamps = 0,
  predictionBounds = rep(FALSE, 2), seeds = NA, adaptive = list(min = 5,
  alpha = 0.05, method = "gls", complete = TRUE), trim = FALSE,
  allowParallel = TRUE)
  
train(x, data, method = "lvq", preProcess = " ",
  trControl = trainControl(), tuneGrid = NULL)

```
```

### Arguments

```
```

preProcess = 
; A string vector that defines a pre-processing of the predictor data
trainControl = 
; A list of values that define how this function acts
varImp
; A generic method for calculating variable importance for objects produced by train and method specific methods

```

### Value
ROC features important rank.

### Author(s)
Zhixing Zhu(981164372@qq.com)

### Examples

```
# If you need to show features important rank by using sample data
#loading dataset
data(PimaIndiansDiabetes)
# prepare training scheme
control <- trainControl(method="repeatedcv", number=10, repeats=3)
# train the model
model <- train(diabetes~., data=PimaIndiansDiabetes, method="lvq", preProcess="scale", trControl=control)
# estimate variable importance
importance <- varImp(model, scale=FALSE)
# summarize importance
print(importance)
# plot importance
plot(importance)

```
