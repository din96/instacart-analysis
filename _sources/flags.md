# Flags


## 4.1.: Intro to Programming for DA
- R vs Python
- Setting up environment 
    - Terminal 
    - Anaconda
    - Launching Jupyter
## 4.2: Jupyter Fundamentals & Python Data Types
- Organizing a Project Folder
- Jupyter
    - Creating Notebooks in Jupyter
    - Creating Cells
    - Deleting Cells
    - Creating Markdown Fields
    - Naming Your Notebook
    - Closing Notebooks
- Python Libraries
- Data types
    - Integer: Numeric data without a decimal point (1, 2, 3, etc.)
    - Floating-Point Number: Numeric data with a decimal point (1.34, 4.567, 10.4, etc.)
    - String: Any textual data
    - Boolean: Data used to denote the truthfulness of a condition or statement. It takes two values: True and False
- Procedures with Data Types
## 4.3: Intro to Pandas

- Pandas Fundamentals
    - Python Data Structures: Dataframes
- Importing a Data Set in Jupyter **orders.csv** and **products.csv**
`df = pd.read_csv(r'folderpath\name.csv', index_col = False,  nrows=1000)`

- Python Shortcut for Importing Data Files
`path = r'folderpath/`

- Exploring Data with Pandas
    - print()
    - df.head()
    - df.tail()
    - info()
    - df.dtypes
   -  describe()
   - df.columns

- Python Data Structures: Lists
Once you’ve identified your unnecessary columns, you can import your data set as a list, leaving off those unnecessary columns. Take a look at the following code that lists all the columns in the “orders.csv” data set except for “eval_set”:

vars_list = ['order_id', 'user_id', 'order_number', 'order_dow', 'order_hour_of_day', 'days_since_prior_order']

You now have a list, vars_list, of all the columns you want to import. All that’s left to do is import your data set again, only this time, with an additional argument telling Python to only import the columns in your list. This can be done via the usecols argument. Take a look at the full command below:

`df = pd.read_csv(os.path.join(path, '02 Data', 'Original Data', 'orders.csv'), usecols = vars_list)`
## 4.4: Data Wrangling & Subsetting 
- Data Wrangling Procedures 
    - Dropping columns: `df.drop(columns = ['variable'])`
    - df['variable'].value_counts(dropna = False)
    - value_counts()
    - Renaming col: df.rename(), df.rename(columns = {'old_name' : 'new_name'}, inplace = True)
    - Changing dtypes: df_ords['order_id'] = df_ords['order_id'].astype('str')
    - Transposing data: df_dep.T, reset_index()
    - iloc[] (“locate an integer” = iloc.)
    - df_dep_t_new = df_dep_t[1:] - from the first row onward
- Data Dictionaries
    - to_dict(), print(data_dict.get('19'))
- Subsetting
    - df_snacks =  df_prods[df_prods['department_id']==19]
    - df_snacks_2 = df_prods.loc[df_prods['department_id'] == 19]
    - df_snacks_3 = df_prods.loc[df_prods['department_id'].isin([19])]
- Exporting Dataframes (orders_wrangeled.csv)
## 4.5: Data Consistency Checks
- What are Data Consistency Checks? 
- Mixed-Type Data
`df_test = pd.DataFrame()`
`df_test['mix'] = ['a', 'b', 1, True]`
"for col in df_test.columns.tolist():
  weird = (df_test[[col]].applymap(type) != df_test[[col]].iloc[0].apply(type)).any(axis = 1)
  if len (df_test[weird]) > 0:
    print (col)"df_test['mix'] = df_test['mix'].astype('str')
    - Missing values 
    - df_prods.isnull().sum()
    - df_nan = df.prods[df_prods['product_name'].isnull() == True]

- Addressing Missing Values

    - Create a new variable that acts like a flag based on the missing value.
    - - df['column with missings'].fillna(median value, inplace=True)
    - Impute the value with the mean or median of the column (if the variable is numeric).
    - Remove or filter out the missing data.
    - df_prods.dropna(subset = [‘product_name’], inplace = True)
    - df_prods.dropna(inplace = True)

- Duplicates 
    - Finding duplicates
    - df_dups = df_prods_clean[df_prods_clean.duplicated()]
    - Addressing Duplicates
    - df_prods_clean_no_dups = df_prods_clean.drop_duplicates()
## 4.6: Combining & Exporting Data
- Methods for Combining Data
    - Concatenating Data pd.concat(), df_concat = pd.concat(frames, axis = 1)
    - Joining Data df.join()
    - Merging Data df.merge(),  df.merge(df_2, on = 'customer_id')
- Merging Your Instacart Data: df_merged_large = df_ords.merge(df_ords_prior, on = 'order_id', indicator = True)
- Exporting Data in Pickle Format

```
# Export data to csv

df_merged_large.to_csv(os.path.join(path, '02 Data','Prepared Data', 'orders_products_combined.csv'))

# Export data to pkl

df_merged_large.to_pickle(os.path.join(path, '02 Data','Prepared Data', 'orders_products_combined.pkl'))
```


## 4.7: Deriving New Variables (FLAGS)
- Deriving Variables
- If-Statements
- If-Statements with User-Defined Functions
- flag 
```
def price_label(row):

  if row['prices'] <= 5:
    return 'Low-range product'
  elif (row['prices'] > 5) and (row['prices'] <= 15):
    return 'Mid-range product'
  elif row['prices'] > 15:
    return 'High range'
  else: return 'Not enough data'
  ```
  - df.apply(price_label, axis=1).
  - value_counts()
  - max()
  ```
  df.loc[df['prices'] > 15, 'price_range_loc'] = 'High-range product'
df.loc[(df['prices'] <= 15) & (df['prices'] > 5), 'price_range_loc'] = 'Mid-range product' 
df.loc[df['prices'] <= 5, 'price_range_loc'] = 'Low-range product'

```
- If-Statements with For-Loops
```
result = []

for value in ords_prods_merge["orders_day_of_week"]:
  if value == 0:
    result.append("Busiest day")
  elif value == 4:
    result.append("Least busy")
  else:
    result.append("Regularly busy")```

## 4.8: Grouping Data & Aggregating Variables
4.8: Grouping Data & Aggregating Variables


- Grouping Data : `df.groupby('product_name')`
- Grouping Data with pandas    
- Aggregating Data with `agg()`
```
df.groupby('department_id').agg({'order_number': ['mean']})
```
- Performing multioply aggregation 
`df.groupby('department_id').agg({'order_number': ['mean', 'min', 'max']})`
- Aggregating Data with transform()
```
ords_prods_merge['max_order'] = ords_prods_merge.groupb
pd.options.display.max_rows = None
```

- Deriving Columns with loc()

```
ords_prods_merge.loc[ords_prods_merge['max_order'] > 40, 'loyalty_flag'] = 'Loyal customer'
ords_prods_merge.loc[(ords_prods_merge['max_order'] <= 40) & (ords_prods_merge['max_order'] > 10), 'loyalty_flag'] = 'Regular customer'
ords_prods_merge.loc[ords_prods_merge['max_order'] <= 10, 'loyalty_flag'] = 'New customer'
```
- Task  
    - Non-frequent customer/Regular customer/Frequent customer


## 4.9: Intro to Data Visualization with Python
- Types of Charts
- Installing and Importing Visualization Libraries - seaborn, matplotlib, scipy
`conda install seaborn matplotlib scipy`
- Creating Bar Charts
`ords_prods_merge['orders_day_of_week'].value_counts().sort_index().plot.bar(color="blue")`
- Exporting Charts
`bar.figure.savefig(os.path.join(path, '04 Analysis','Visualizations', 'bar_orders_dow.png'))`
- Creating Histograms and Scatterplots (PRICE column issue solution)
`ords_prods_merge['prices'].plot.hist(bins = 25)`
`sns.scatterplot(x = 'prices', y = 'prices',data = ords_prods_merge)`
- Creating Line Charts
- Creating Line Charts
`np.random.seed(4)
dev = np.random.rand(len(ords_prods_merge)) <= 0.7`
```
big = ords_prods_merge[dev]
small = ords_prods_merge[~dev]
df_2 = small[['orders_day_of_week','prices']]
```
`line = sns.lineplot(data = df_2, x = 'orders_day_of_week',y = 'prices')`

- **TASK CUSTOMERS FRAME** 
- histogram of the “order_hour_of_day” 
- a bar chart from the “loyalty_flag” column.
- Check whether there’s a difference in expenditure (the “prices” column) depending on the hour of the day. (Hint: To check this, you need to use an accurate sample for your line chart!)
- explore whether there’s a connection between age and spending power (income). To visualize this relationship, create a scatterplot using the sns.scatterplot()

## 4.10
- Coding Best Practices
    - Maintaining Clean and Concise Scripts
    - Avoiding the Overwrite

- Storing Useful Resources
- Jupyter Tips and Tricks
    - Clearing Outputs
    - Stopping a Procedure from Executing
    - Restarting the Kernel
- Using Excel with Python
    - Crosstabs in Python
    `crosstab.to_clipboard()`
    - Confirming with Stakeholders
    - Python Text Editor
- Data Security
- Instacart Analysis Final Report
    - Population Flows
    - Data Citation
- Non-Technical Skills
    - Skepticism and Critical Thinking
    - Precision
    - Communication
    - Domain Expertise


