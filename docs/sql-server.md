# SQL Server

## Drop Procedure if Exists

```SQL
IF EXISTS
(
    SELECT 1
    FROM sysobjects
    WHERE id = object_id(N'[dbo].[proc]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1
)
BEGIN
	DROP PROCEDURE [dbo].[proc]
END
GO
```

## Drop Table if Exists

```SQL
IF EXISTS
(
    SELECT 1
    FROM INFORMATION_SCHEMA.TABLES
    WHERE TABLE_SCHEMA = '<schema>' AND TABLE_NAME = '<table>'
)
BEGIN
	DROP TABLE [<schema>].[<table>]
END
GO
```

## Insert or Update Row Using MERGE

```SQL
MERGE table_name AS target
USING (SELECT @var1, @var2, @var3) AS source (col1, col2, col3)
ON (target.col1 = source.col1) -- Conditions comparing "target" and "source"
WHEN MATCHED THEN
    UPDATE SET target.col1 = source.col1 -- Update "target" from "source"
WHEN NOT MATCHED BY TARGET THEN
    INSERT (col1, col2, col3)
    VALUES (source.col1, source.col2, source.col3) -- Insert new row from "source"
```

## SET NOCOUNT ON

`SET NOCOUNTON` prevents the message from showing which contains the number of affected rows. Using this in a stored procedure can significantly improve its performance.
