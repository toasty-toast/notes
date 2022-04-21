# Oracle DB

## List a Table's Columns and Their Types

```SQL
SELECT COLUMN_NAME, DATA_TYPE, DATA_LENGTH
FROM ALL_TAB_COLUMNS
WHERE TABLE_NAME = '<table>'
ORDER BY COLUMN_NAME
```