# Data Dictionary

## Population Flow

<iframe src="https://miro.com/app/live-embed/uXjVMHuEmqI=/?moveToViewport=-1384,-761,2929,1521&embedId=898286255048" scrolling="no" allow="fullscreen; clipboard-read; clipboard-write" allowfullscreen width="768" height="432" frameborder="0"></iframe>

## Data Frames

## instacart-data
Final Dataframe
````{card} 
instacarrt-data(rows:32404859, columns:24)
^^^
:::{list-table}
:header-rows: 1

*   - Column name
    - Data type
    - Description
    - Label
*   - `order_id` {bdg-warning}`key`
    - `str`
    - Order identifier. 
    - 
*   - `user_id` {bdg-warning}`key`
    - `str`
    - User identifier.
    - 
*   - `order_number`
    - `int64`
    - Number of the order.
    - 
*   - `orders_day_of_week`
    - `int64`
    - Day of the week.
    - {bdg-info}`0 = Sat`
*   - `order_hour_of_day`
    - `int64`
    - Hour of the order
    - {bdg-info}`24h`
*   - `days_since_prior_order`
    - `float64`
    - Days since the last order, capped at 30 (with NAs for order_number = 1).
    - 
*   - `new_customer`
    - `bool`
    - First order after the signup flag.
    - {bdg-info}`flag`
*   - `product_id` {bdg-warning}`key`
    - `str`
    - Product identifier. 
    - 
*   - `add_to_cart_order`
    - `int64`
    - Products were put into the cart.
    - 
*   - `reordered`
    - `int64`
    - Reorder information. 1-reordered 0-not reorderd.
    - 
*   - `product_name`
    - `str`
    - Product name.
    - 
*   - `gender`
    - `str`
    - Gender. Column name updated
    - 
*   - `aisle_id`
    - `str`
    - Aisle identificator.
    - 
*   - `department_id`
    - `str`
    - Department identificator. 
    -
*   - `prices`
    - `float64`
    - Product price.
    - 
*   - `price_range`
    - `str`
    - TO DO 
    - TO DO 
*   - `price_range_loc`
    - TO DO 
    - TO DO 
    - TO DO 
*   - `busiest_hours`
    - TO DO 
    - TO DO 
    - TO DO 
*   - `state`
    - `str`
    - State of USA. Column name updated
    - {bdg-info}`updated`
*   - `signup_date`
    - `str`
    - Date of user signup. Column name changed.
    - {bdg-info}`updated`
*   - `income`
    - `int64`
    - Users income
    - 
*   - `region`
    - `str`
    - USA region.
    - {bdg-info}`flag`
:::
Download .csv
````


## -------




## customers
:::::{tab-set}
::::{tab-item} Current version
:::{card}
customers (206209 rows, 6 columns):
^^^
:::{list-table}
:header-rows: 1
*   - Column name
    - Data type
    - Description
    - Log
*   - `user_id` {bdg-warning}`key`
    - `str` 
    - User identifier 
    - 
*   - `gender`
    - `str`
    - Gender. Column name updated
    - {bdg-info}`updated`
*   - `gender`
    - `str`
    - Gender. Column name updated
    - {bdg-info}`updated`
*   - `state`
    - `str`
    - State of USA. Column name updated
    - {bdg-info}`updated`
*   - `signup_date`
    - `str`
    - Date of user signup. Column name changed.
    - {bdg-info}`updated`
*   - `income`
    - `int64`
    - Users income
    - 
*   - `region`
    - `str`
    - State region. 
    - {bdg-success}`new`
:::
::::
::::{tab-item} Raw
:::{card}
customers (206209 rows, 10 columns):
^^^
:::{list-table}
:header-rows: 1
*   - Column name
    - Data type
    - Description
    - Log
*   - `user_id` {bdg-warning}`key`
    - `str`
    - User identifier 
    - 
*   - `first_name`
    - `str`
    - First name of the user. PII, dropping.
    - {bdg-danger}`dropped`
*   - `last_name`
    - `str`
    - Last name of the user. PII, dropping.
    - {bdg-danger}`dropping`
*   - `gender`
    - `str`
    - Gender. Column name updated.
    - {bdg-info}`updating`
*   - `state`
    - `str`
    - State of USA. Unifying column name.
    - {bdg-info}`updating`
*   - `family_status`
    - `str`
    - Family status of the user. Unifying column name. 
    - {bdg-danger}`dropping`
*   - `signup_date`
    - `str`
    - Date of user signup. Changing column name.
    - {bdg-info}`updating`
*   - `n_dependands`
    - `int64`
    - Number of family members. Corrupt, dropping.
    - {bdg-info}`updating`
*   - `income`
    - `int64`
    - Users income
    - 
:::
::::
:::::


## departments
:::::{tab-set}
::::{tab-item} Current version
:::{card}
departments (22 rows, 2 columns):
^^^
:::{list-table}
:header-rows: 1
*   - Column name
    - Data type
    - Description
    - Log
*   - `department_id` {bdg-warning}`key`
    - `str`
    - Department identificator.
    - {bdg-success}`new`
*   - `department`
    - `str`
    - Department name.
    - {bdg-success}`new`
:::
::::
::::{tab-item} Current version
:::{card}
departments (1 row, 22 columns):
^^^
:::{list-table}
:header-rows: 1
*   - Column name
    - Data type
    - Description
    - Log
*   - `index`
    - `str`
    - Dataframe index. Transposing data.
    - {bdg-info}`updating`
:::
::::
:::::

## orders

:::::{tab-set}
::::{tab-item} Current version
:::{card}
orders (3421083 rows, 7 columns):
^^^
:::{list-table}
:header-rows: 1
*   - Column name
    - Data type
    - Description
    - Log
*   - `order_id` {bdg-warning}`key`
    - `str`
    - Order identificator. Changed datatype.
    - {bdg-info}`changed-dtype`
*   - `user_id` {bdg-warning}`key`
    - `str`
    - User identificator. Changed datatype.
    - {bdg-info}`changed-dtype`
*   - `order_number`
    - `int64`
    - Order number. Changed datatype.
    - {bdg-info}`changing-dtype`
*   - `order_day_of_week`
    - `int64`
    - Order day of week. Changed column name.
    - {bdg-info}`changed-name`
*   - `order_hour_of_day`
    - `int64`
    - Order day of day.
    - 
*   - `days_since_prior_order`
    - `float64`
    - Days since prior order. NaN is the first order after sign up
    - 
*   - `new_customer`
    - `bool`
    - New customer flag.
    - {bdg-success}`new`
:::
::::
::::{tab-item} Raw
:::{card}
orders (3421083 rows, 7 columns):
^^^
:::{list-table}
:header-rows: 1
*   - Column name
    - Data type
    - Description
    - Log
*   - `order_id` {bdg-warning}`key`
    - `int64`
    - Order identificator. Changing datatype.
    - {bdg-info}`changing-dtype`
*   - `user_id` {bdg-warning}`key`
    - `int64`
    - User identificator. Changing datatype.
    - {bdg-info}`changing-dtype`
*   - `eval_set`
    - `object`
    - Evaluation for ML. Irrelevant, dropping.
    - {bdg-warning}`dropping`
*   - `order_number`
    - `int64`
    - Order number. Changing datatype.
    - {bdg-info}`changing-dtype`
*   - `order_dow`
    - `int64`
    - Order day of week. Changing column name.
    - {bdg-info}`changing-name`
*   - `order_hour_of_day`
    - `int64`
    - Order day of day.
    - 
*   - `days_since_prior_order`
    - `float64`
    - Days since prior order. NaN is the first order after sign up
    - 
:::
::::
:::::

## products
:::::{tab-set}
::::{tab-item} Current version
:::{card}
products (49672 rows, 4 columns):
^^^
:::{list-table}
:header-rows: 1
*   - Column name
    - Data type
    - Description
    - Log
*   - `product_id` {bdg-warning}`key`
    - `str`
    - Product identificator. 
    - {bdg-info}`changed-dtype`
*   - `product_name`
    - `str`
    - Product name.
    - 
*   - `department_id` {bdg-warning}`key`
    - `str` 
    - Department identificator.
    - {bdg-info}`changed-dtype`
*   - `prices`
    - `float64`
    - Product price in USD
    - 
:::
::::
::::{tab-item} Raw version
:::{card}
products (49693 rows, 5 columns):
^^^
:::{list-table}
:header-rows: 1
*   - Column name
    - Data type
    - Description
    - Log
*   - `product_id` {bdg-warning}`key`
    - `int64`
    - Product identificator. Changing data type.
    - {bdg-info}`changing-dtype`
*   - `product_name`
    - `str`
    - Product name.
    - 
*   - `aisle_id`
    - `int64`
    - Aisle indetificator. Irrelevant, dropping.
    - {bdg-danger}`dropping`
*   - `department_id` {bdg-warning}`key`
    - `int64` 
    - Department identificator. Changing data type
    - 
*   - `prices`
    - `float64`
    - Product price in USD. 
    - {bdg-info}`changing-dtype`
:::
::::
:::::

## product-orders-prior
:::::{tab-set}
::::{tab-item} Current version
:::{card}
order-products-prior (32434489 rows, 4 columns):
^^^
:::{list-table}
:header-rows: 1
*   - Column name
    - Data type
    - Description
    - Log
*   - `order_id` {bdg-warning}`key`
    - `str`
    - Order identificator. Changed data type.
    - {bdg-info}`changed-dtype`
*   - `product_id` {bdg-warning}`key`
    - `str`
    - Product identificator. Changed data type.
    - {bdg-info}`changed-dtype`
*   - `add_to_cart_order`
    - `int64`
    - 
    - 
*   - `reordered`
    - `int64`
    - Number of reorders.
    - 
:::
::::
::::{tab-item} Raw version
:::{card}
order-products-prior (32434489 rows, 4 columns):
^^^
:::{list-table}
:header-rows: 1
*   - Column name
    - Data type
    - Description
    - Log
*   - `order_id` {bdg-warning}`key`
    - `int64`
    - Order identificator. Changing data type.
    - {bdg-info}`changing-dtype`
*   - `product_id` {bdg-warning}`key`
    - `int64`
    - Product identificator. Changing data type.
    - {bdg-info}`changing-dtype`
*   - `add_to_cart_order`
    - `int64`
    - 
    - 
*   - `reordered`
    - `int64`
    - Number of reorders.
    - 
:::
::::
:::::