# Convert trained XGBoost model to SQL

This tool enables in-database scoring of XGBoost model built in R. To use this function, call `fun_xgboost_to_sql()` and pass the trained XGBoost model, name of the ouput SQL file, name of the input database table, and name of the unique key of that table. Output of the function is a SQL script.

### Prerequisites

```
install.packages("xgboost")
install.packages("stringr")
```

### Usage:

```
xgbFit = xgboost(data = x, nfold = 5, label = y, 
                 nrounds = 10, verbose = T, objective = "binary:logistic", 
                 nthread = 8, eta = 0.01, gamma = 0.0468, max_depth = 6, min_child_weight = 1.7817, 
                 subsample = 0.5213, colsample_bytree = 0.4603)
                 
fun_xgboost_to_sql(xgbFit,"output.SQL","[database].[tablename]","id")
```
`booster [default= gbtree ]` is only supported.
### Supported objective functions:

Following XGBoost objective functions are supported:
```
objective = "binary:logistic"
          = "reg:logistic"
          = "reg:linear"
          = "reg:gamma"
          = "count:poisson"
          = "reg:tweedie"
```
