Q: write query to select second max value in certain column from a table.

A: There are at least three ways to deal with this question. If there is no duplicate of max, then S1S2S3 all works, otherwise S1S2 works.

S1 find the max value which is smaller the overall 'max'.

```sql
SELECT MAX( col )
FROM table
WHERE col < (SELECT MAX( col )
             FROM table)
```

S2 find the max value from the table where the original max is gone/excluded.

```sql
SELECT MAX(col) 
FROM table 
WHERE col NOT IN (SELECT MAX(col)
                  FROM table)
```

S3 sort/order the table and select/return what we want

```sql
SELECT col FROM table
ORDER BY col DESC
LIMIT 1,1
```
