Sizwe Coffee SQL Assignment

## Project overview

This project looks at two years of sales data for Sizwe Coffee, a company that sells coffee to businesses through two channels, Wholesale and Subscription. The finance director and the sales manager had questions before their year-end meeting, and I answered eight of them using SQL.

The questions were about:

1. Sales by channel and how much each grew
2. Profit and margin for each product line
3. How quickly each channel pays and how much is still owed
4. The ten biggest customers
5. Big Wholesale customers who never got a promotion
6. Whether the sales reps hit their targets
7. How sales change from month to month
8. Why the margin went down

All my queries and answers are in [`queries.sql`](queries.sql).

## Dataset

I used seven tables: `customers`, `products`, `sales_orders`, `sales_lines`, `ar_ledger`, `reps` and `trade_promotions`.

This is how I joined them:

- Orders and order lines, on `order_id`
- Order lines and products, on `sku`
- Orders, invoices and promotions to customers, on `customer_id`
- Orders and customers to reps, on `rep_id`

Some orders had no date or no channel, so I left them out in the tasks that needed a date or channel (Tasks 1, 7 and 8).

## Skills demonstrated

- Joins, including left joins so that no customer or rep was left out (Tasks 4 and 6)
- A left join with `is null` to find customers with no promotion (Task 5)
- `sum`, `count`, `avg` and `group by` (all tasks)
- `case when` to split sales into FY2024 and FY2025 (Tasks 1 and 8)
- `coalesce`, `try_divide` and `is not null` to deal with blanks (Tasks 1, 4, 6, 7 and 8)
- Date functions `datediff` and `date_trunc` (Tasks 3 and 7)
- `with` (CTEs) to build a summary first (Tasks 1, 7 and 8)
- Window functions `lag` and `sum() over` (Tasks 7 and 8)
- `order by` and `limit` for top lists (Tasks 2, 4, 5 and 6)

## How to run

1. Load the Sizwe Coffee tables into Databricks. My tables start with `sizwe_`.
2. Open a SQL notebook.
3. Copy the queries from `queries.sql` and run them one at a time.



## Key insights

### For Nomsa

- Both channels grew by 8.8%. Wholesale went from R308.2m to R335.4m and Subscription from R132.8m to R144.6m.
- House Blend makes the most profit (R107.1m), but Single Origin has the best margin (44.3%). Bulk Commercial has the lowest margin at 19.9%.
- The margin went down because Sizwe sold a lot more Bulk Commercial, its lowest-margin line. Its sales grew from R110.3m to R161.5m, and its share of sales went from 25.0% to 33.6%. Each line's own margin hardly changed.
- Wholesale customers are slow to pay. They take about 69 days, compared to about 4 days for Subscription, and they still owe R87.8m on 3,454 open invoices.
- Sales are highest in June and July and lowest in December, and this happened in both years.

### For Bongani

- Umhlanga Fresh 108 (R6.2m), Ridgeway Foods 308 (R4.4m) and Kalahari Kitchen 42 (R4.4m) are big Wholesale customers that have never had a promotion. I would offer them a once-off 10% discount on their next order.
