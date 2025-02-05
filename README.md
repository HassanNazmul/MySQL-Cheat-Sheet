# SQL Cheat Sheet

## Basic SQL Commands
- **SELECT** - Retrieves data from a database
    ```sql
    SELECT column1, column2 FROM table_name;  -- Selects specified columns from the table
    ```
- **INSERT INTO** - Adds new data into a database
    ```sql
    INSERT INTO table_name (column1, column2)  -- Specifies target table and columns
    VALUES (value1, value2);                   -- Provides values to insert
    ```
- **UPDATE** - Modifies existing data within a database
    ```sql
    UPDATE table_name                -- Specifies table to update
    SET column1 = value1            -- Sets new values for columns
    WHERE condition;                -- Filters which rows to update
    ```
- **DELETE** - Removes data from a database
    ```sql
    DELETE FROM table_name          -- Specifies table to delete from
    WHERE condition;                -- Filters which rows to delete
    ```

## Filtering Data
- **WHERE** - Filters records based on a specified condition
    ```sql
    SELECT column1, column2 FROM table_name     -- Selects columns
    WHERE condition;                            -- Filters rows based on condition
    ```
- **AND, OR, NOT** - Combines multiple conditions
    ```sql
    SELECT * FROM table_name                    -- Selects all columns
    WHERE condition1 AND condition2;            -- Both conditions must be true
    ```
- **IN** - Checks if a value exists within a set of values
    ```sql
    SELECT * FROM table_name                    -- Selects all columns
    WHERE column_name IN (value1, value2);      -- Matches any value in the list
    ```
- **BETWEEN** - Filters data within a given range
    ```sql
    SELECT * FROM table_name                    -- Selects all columns
    WHERE column_name BETWEEN value1 AND value2; -- Matches values in range
    ```
- **LIKE** - Searches for a specified pattern in a column
    ```sql
    SELECT * FROM table_name                    -- Selects all columns
    WHERE column_name LIKE 'pattern%';          -- Matches pattern with wildcard
    ```
- **IS NULL, IS NOT NULL** - Checks for NULL (or non-NULL) values
    ```sql
    SELECT * FROM table_name                    -- Selects all columns
    WHERE column_name IS NULL;                  -- Matches NULL values
    ```
- **EXISTS** - Checks if a subquery returns any records
    ```sql
    SELECT * FROM table_name                    -- Selects all columns
    WHERE EXISTS (SELECT * FROM another_table); -- Checks subquery results
    ```

## Sorting and Limiting Data
- **ORDER BY** - Sorts the result set by one or more columns
    ```sql
    SELECT * FROM table_name                    -- Selects all columns
    ORDER BY column1 ASC, column2 DESC;         -- Sorts by column1 ascending, column2 descending
    ```
- **LIMIT** - Specifies the number of records to return
    ```sql
    SELECT * FROM table_name                    -- Selects all columns
    LIMIT 10;                                   -- Returns only first 10 records
    ```
- **DISTINCT** - Returns only distinct (unique) values
    ```sql
    SELECT DISTINCT column1 FROM table_name;    -- Returns unique values from column1
    ```

## Aggregating Data
- **COUNT()** - Counts the number of rows
- **SUM()** - Calculates the sum of a numeric column
- **AVG()** - Calculates the average value of a numeric column
- **MIN()** - Finds the minimum value in a column
- **MAX()** - Finds the maximum value in a column
- **GROUP BY** - Groups rows that have the same values in specified columns
- **HAVING** - Filters groups based on a specified condition

## Joins
- **INNER JOIN** - Returns records with matching values in both tables
- **LEFT JOIN** (LEFT OUTER JOIN) - Returns all records from the left table, and matched records from the right table
- **RIGHT JOIN** (RIGHT OUTER JOIN) - Returns all records from the right table, and matched records from the left table
- **FULL JOIN** (FULL OUTER JOIN) - Returns all records when there is a match in either left or right table
- **CROSS JOIN** - Returns the Cartesian product of two tables
- **SELF JOIN** - Joins a table with itself

## Subqueries
- Subqueries in **SELECT** - Retrieves data in a subquery used within a SELECT statement
- Subqueries in **WHERE** - Uses a subquery to filter data within a WHERE clause
- Subqueries in **FROM** - Uses a subquery within the FROM clause

## Set Operations
- **UNION** - Combines the results of two or more SELECT statements, excluding duplicates
- **UNION ALL** - Combines the results of two or more SELECT statements, including duplicates
- **INTERSECT** - Returns only the records that appear in both result sets
- **EXCEPT** - Returns the records in the first result set that are not in the second

## Data Modification
- **INSERT** - Adds new records to a table
- **UPDATE** - Modifies existing records in a table
- **DELETE** - Removes records from a table

## Indexing
- **CREATE INDEX** - Creates an index on a table
- **DROP INDEX** - Deletes an index from a table
- **UNIQUE INDEX** - Creates a unique index on a table
- **FULL-TEXT INDEX** - Creates a full-text index on a table
- **COMPOSITE INDEX** - Creates an index on multiple columns

## Transactions
- **BEGIN TRANSACTION** - Starts a database transaction
- **COMMIT** - Saves the changes made in a transaction
- **ROLLBACK** - Undoes the changes made in a transaction
- **SAVEPOINT** - Sets a savepoint within a transaction
- **SET TRANSACTION** - Sets the characteristics of the current transaction
- **ISOLATION LEVEL** - Sets the isolation level for the current transaction

## Views
- **CREATE VIEW** - Creates a view
- **DROP VIEW** - Deletes a view
- **ALTER VIEW** - Modifies a view
- **INSERT INTO VIEW** - Adds records to a view
- **UPDATE VIEW** - Modifies records in a view

## Triggers
- **CREATE TRIGGER** - Creates a trigger
- **DROP TRIGGER** - Deletes a trigger
- **AFTER INSERT/UPDATE/DELETE** - Executes after a specific operation
- **BEFORE INSERT/UPDATE/DELETE** - Executes before a specific operation

## Common Table Expressions
- **WITH CTE AS** - Defines a common table expression (CTE)
- **RECURSIVE CTE** - Defines a recursive common table expression
- **WITH TEMPORARY CTE** - Defines a temporary common table expression

## Window Functions
- **ROW_NUMBER()** - Assigns a unique number to each row
- **RANK()** - Assigns a rank to each row within a partition
- **DENSE_RANK()** - Similar to RANK(), but no gaps in ranking values
- **NTILE()** - Distributes rows into a specified number of buckets
- **LEAD()** - Accesses data from the following row
- **LAG()** - Accesses data from the preceding row
- **FIRST_VALUE()** - Returns the first value in an ordered set
- **LAST_VALUE()** - Returns the last value in an ordered set
- **SUM() OVER()** - Computes the sum over a specified window
- **AVG() OVER()** - Computes the average over a specified window
- **PARTITION BY** - Divides the result set into partitions
- **ORDER BY** (WITHIN WINDOW FUNCTION) - Specifies the order of rows within a partition

## Date and Time Functions
- **GETDATE()** - Returns the current date and time
- **CURRENT_TIMESTAMP** - Returns the current date and time
- **DATEADD()** - Adds a specified number of units to a date
- **DATEDIFF()** - Calculates the difference between two dates
- **DATEPART()** - Returns a specified part of a date
- **DATE_FORMAT()** - Formats a date value
- **NOW()** - Returns the current date and time
- **EXTRACT()** - Extracts a specified part of a date
- **TIMESTAMPDIFF()** - Returns the difference between two timestamps

## Conditional Logic
- **CASE WHEN** - Evaluates a list of conditions and returns one of multiple possible result expressions
- **IFNULL()** - Returns a specified value if the expression is NULL
- **COALESCE()** - Returns the first non-NULL value in a list of expressions
