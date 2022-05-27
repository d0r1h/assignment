### Product Data Analysis


# 

### Speeding data loading using `Pandas`

As the size of the data is 1.3 GB on the disk and sample size is more than 13 million, It will take time to load into memory. So to save memory size and speed up the data loading process, run the following code.

```python
data = pd.read_csv("/content/test/2022_02_08-02_30_31_AM.csv", nrows=5)  #load only first 5 rows
data.dtypes  # get the data types of columns
dtypes = dict(zip(data.columns.values, ['object', 'object', 'object', 'object', 'object', 'object']))  # zip the data types and store into a vaiable
json.dumps(dtypes) # dump into josn format
del data  # delete the variable from the ram 
data = pd.read_csv("/content/test/2022_02_08-02_30_31_AM.csv", dtype=dtypes) # load whole dataset with data type parameter
```
The following table summarizes wall time:

| Approach | Time 
|------|------|
| directly loading | 23.2 s | 
| data loading with mentioned data type | 16.7 s | 

### Features from the data

1. uuid                 
2. price_string         
3. price_string_unf   
4. product_type         
5. level_1              
6. category 


### Insights from data 

1. There are `~13 million` data points and 6 features.
2. There are two features that have more than `50%` missing values.
3. There are `~8 million` products that do not have price value.
4. There are total `278` product_type that have no price.
5. For any product category maximum count is `140k` and the minimum is `10k`.
6. There are only 2 product categories whose price is more than 100$.


### Install the Dependencies 

```
!pip install -r requirements.txt
```

### There are total 4 questions answered

1. Products without prices
2. Count of products without prices and with prices in each Product Type, Category, Level 1
3. Correct Product Prices in the correct format (eg: $56) wherever possible and separate them into currency and value columns.
4. List out the categories with average price of product.
