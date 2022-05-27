### Product Data Analysis


# 

### Speeding data loading using `Pandas`

As the size of the data is on the disk and sample size is more than 13 million, It gonna take a time to load into memory and also consume a lot of memoery size. So to save memory size and speeding up the data loading run the following code.

```python
data = pd.read_csv("/content/test/2022_02_08-02_30_31_AM.csv", nrows=5)  #load only first 5 rows
data.dtypes  # get the data types of columns
dtypes = dict(zip(data.columns.values, ['object', 'object', 'object', 'object', 'object', 'object']))  # zip the data types and store into a vaiable
json.dumps(dtypes) # dump into josn format
del data  # delete the variable from the ram 
data = pd.read_csv("/content/test/2022_02_08-02_30_31_AM.csv", dtype=dtypes) # load whole dataset with data type parameter
```
Following table summarizes wall time:

| Approach | Time 
|------|------|
| directly loading | 23.2 s | 
| data loading with mentioned data type | 16.7 s | 


### Insights from data 

1. There are `~13 million` data points and 6 features.
2. There are two features who have more than of `50%` missing values.
3. There are `~8 million` products that does not have price.
4. There are total `278` product categories which have no price.
5. For any prodct category max count is `140k` and minimum is `10k`.
