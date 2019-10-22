# SQL Server

## Check If Column Exists

```SQL
IF EXISTS (SELECT 1 FROM sys.columns WHERE name = 'column' AND object_id = OBJECT_ID('schema.table'))
BEGIN
    -- The column exists
END
```

## Check If Index Exists

```SQL
IF EXISTS (SELECT 1 FROM sys.indexes WHERE name = 'index_name' AND object_id = OBJECT_ID('table_name'))
BEGIN
    -- The index exists
END
```

## Check If Procedure Exists

```SQL
IF EXISTS (SELECT 1 FROM sysobjects WHERE id = object_id(N'schema.proc') AND OBJECTPROPERTY(id, N'IsProcedure') = 1)
BEGIN
    -- The procedure exists
END
```

## Check If Table Exists

```SQL
IF EXISTS (SELECT 1 FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA = 'schema' AND TABLE_NAME = 'table')
BEGIN
    -- The table exists
END
```

## Create Procedure

```SQL
CREATE PROCEDURE [schema].[procedure]
    @arg INT,
    @argWithDefault VARCHAR(10) = NULL
AS
BEGIN
    -- Procedure body
END
```

## DATETIME CONVERT() Styles

|Without century|With century|Input/Output|Standard|
|---------------|------------|------------|--------|
|0|100|mon dd yyyy hh:miAM/PM|Default|
|1|101|mm/dd/yyyy|US|
|2|102|yyyy.mm.dd|ANSI|
|3|103|dd/mm/yyyy|British/French|
|4|104|dd.mm.yyyy|German|
|5|105|dd-mm-yyyy|Italian|
|6|106|dd mon yyyy|-|
|7|107|Mon dd, yyyy|-|
|8|108|hh:mm:ss|-|
|9|109|mon dd yyyy hh:mi:ss:mmmAM (or PM)|Default + millisec|
|10|110|mm-dd-yyyy|USA|
|11|111|yyyy/mm/dd|Japan|
|12|112|yyyymmdd|ISO|
|13|113|dd mon yyyy hh:mi:ss:mmm|Europe (24 hour clock)>|
|14|114|hh:mi:ss:mmm|24 hour clock|
|20|120|yyyy-mm-dd hh:mi:ss|ODBC canonical (24 hour clock)|
|21|121|yyyy-mm-dd hh:mi:ss.mmm|ODBC canonical (24 hour clock)|
||126|yyyy-mm-ddThh:mi:ss.mmm|ISO8601|
||127|yyyy-mm-ddThh:mi:ss.mmmZ|ISO8601 (with time zone Z)|
||130|dd mon yyyy hh:mi:ss:mmmAM|Hijiri|
||131|dd/mm/yy hh:mi:ss:mmmAM|Hijiri|

## Get All Database Triggers

```SQL
SELECT TAB.name as TableName, TRIG.name as TriggerName, TRIG.is_disabled AS IsDisabled
FROM sys.triggers AS TRIG
INNER JOIN sys.tables AS TAB
ON TRIG.parent_id = TAB.object_id
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

`SET NOCOUNT ON` prevents the message from showing which contains the number of affected rows. Using this in a stored procedure can significantly improve its performance.
