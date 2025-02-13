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
    ```sql
    SELECT COUNT(*) FROM table_name;           -- Counts total number of rows
    ```
- **SUM()** - Calculates the sum of a numeric column
    ```sql
    SELECT SUM(column_name) FROM table_name;   -- Calculates sum of values in column
    ```
- **AVG()** - Calculates the average value of a numeric column
    ```sql
    SELECT AVG(column_name) FROM table_name;   -- Calculates average of values in column
    ```
- **MIN()** - Finds the minimum value in a column
    ```sql
    SELECT MIN(column_name) FROM table_name;   -- Finds smallest value in column
    ```
- **MAX()** - Finds the maximum value in a column
    ```sql
    SELECT MAX(column_name) FROM table_name;   -- Finds largest value in column
    ```
- **GROUP BY** - Groups rows that have the same values in specified columns
    ```sql
    SELECT column1, COUNT(*) 
    FROM table_name
    GROUP BY column1;                          -- Groups results by column1
    ```
- **HAVING** - Filters groups based on a specified condition
    ```sql
    SELECT column1, COUNT(*) 
    FROM table_name
    GROUP BY column1
    HAVING COUNT(*) > 5;                       -- Filters groups with count > 5
    ```

## Joins
- **INNER JOIN** - Returns records with matching values in both tables
    ```sql
    SELECT * FROM table1                         -- Selects all columns
    INNER JOIN table2                           -- Specifies join type
    ON table1.id = table2.id;                  -- Defines join condition
    ```
- **LEFT JOIN** (LEFT OUTER JOIN) - Returns all records from the left table, and matched records from the right table
    ```sql
    SELECT * FROM table1                         -- Selects all columns
    LEFT JOIN table2                            -- Specifies join type
    ON table1.id = table2.id;                  -- Defines join condition
    ```
- **RIGHT JOIN** (RIGHT OUTER JOIN) - Returns all records from the right table, and matched records from the left table
    ```sql
    SELECT * FROM table1                         -- Selects all columns
    RIGHT JOIN table2                           -- Specifies join type
    ON table1.id = table2.id;                  -- Defines join condition
    ```
- **FULL JOIN** (FULL OUTER JOIN) - Returns all records when there is a match in either left or right table
    ```sql
    SELECT * FROM table1                         -- Selects all columns
    FULL OUTER JOIN table2                      -- Specifies join type
    ON table1.id = table2.id;                  -- Defines join condition
    ```
- **CROSS JOIN** - Returns the Cartesian product of two tables
    ```sql
    SELECT * FROM table1                         -- Selects all columns
    CROSS JOIN table2;                          -- Creates Cartesian product
    ```
- **SELF JOIN** - Joins a table with itself
    ```sql
    SELECT a.column1, b.column2                  -- Selects columns from both instances
    FROM table1 a                               -- First instance of table
    JOIN table1 b                               -- Second instance of same table
    ON a.id = b.parent_id;                     -- Defines join condition
    ```

## Subqueries
- Subqueries in **SELECT** - Retrieves data in a subquery used within a SELECT statement
    ```sql
    SELECT column1,
           (SELECT COUNT(*) FROM table2         -- Subquery in SELECT
            WHERE table2.id = table1.id) as count
    FROM table1;
    ```
- Subqueries in **WHERE** - Uses a subquery to filter data within a WHERE clause
    ```sql
    SELECT * FROM table1                        -- Main query
    WHERE column1 IN                           -- WHERE clause with subquery
          (SELECT column1 FROM table2
           WHERE condition);
    ```
- Subqueries in **FROM** - Uses a subquery within the FROM clause
    ```sql
    SELECT avg_price FROM                       -- Main query
        (SELECT category, AVG(price) as avg_price
         FROM products                         -- Subquery in FROM
         GROUP BY category) AS category_stats;
    ```

## Set Operations
- **UNION** - Combines the results of two or more SELECT statements, excluding duplicates
    ```sql
    SELECT column1 FROM table1               -- First SELECT statement
    UNION                                    -- Combines results, removes duplicates
    SELECT column1 FROM table2;              -- Second SELECT statement
    ```
- **UNION ALL** - Combines the results of two or more SELECT statements, including duplicates
    ```sql
    SELECT column1 FROM table1               -- First SELECT statement
    UNION ALL                               -- Combines results, keeps duplicates
    SELECT column1 FROM table2;              -- Second SELECT statement
    ```
- **INTERSECT** - Returns only the records that appear in both result sets
    ```sql
    SELECT column1 FROM table1               -- First SELECT statement
    INTERSECT                               -- Returns common records only
    SELECT column1 FROM table2;              -- Second SELECT statement
    ```
- **EXCEPT** - Returns the records in the first result set that are not in the second
    ```sql
    SELECT column1 FROM table1               -- First SELECT statement
    EXCEPT                                  -- Returns records unique to first query
    SELECT column1 FROM table2;              -- Second SELECT statement
    ```

## Data Modification
- **INSERT** - Adds new records to a table
    ```sql
    INSERT INTO table_name (column1, column2)  -- Specifies target table and columns
    VALUES (value1, value2);                   -- Provides values to insert
    ```
- **UPDATE** - Modifies existing records in a table
    ```sql
    UPDATE table_name                -- Specifies table to update
    SET column1 = value1            -- Sets new values
    WHERE condition;                -- Specifies which records to update
    ```
- **DELETE** - Removes records from a table
    ```sql
    DELETE FROM table_name          -- Specifies table to delete from
    WHERE condition;                -- Specifies which records to delete
    ```

## Indexing
- **CREATE INDEX** - Creates an index on a table
    ```sql
    CREATE INDEX index_name             -- Creates a new index
    ON table_name (column1, column2);   -- Specifies table and columns to index
    ```
- **DROP INDEX** - Deletes an index from a table
    ```sql
    DROP INDEX index_name              -- Removes the specified index
    ON table_name;                     -- From the specified table
    ```
- **UNIQUE INDEX** - Creates a unique index on a table
    ```sql
    CREATE UNIQUE INDEX index_name     -- Creates index with unique constraint
    ON table_name (column1);          -- On specified table and column
    ```
- **FULL-TEXT INDEX** - Creates a full-text index on a table
    ```sql
    CREATE FULLTEXT INDEX index_name   -- Creates full-text search index
    ON table_name (column1);          -- On specified table and column
    ```
- **COMPOSITE INDEX** - Creates an index on multiple columns
    ```sql
    CREATE INDEX index_name           -- Creates multi-column index
    ON table_name (col1, col2, col3); -- On specified columns in order
    ```

## Transactions
- **BEGIN TRANSACTION** - Starts a database transaction
    ```sql
    BEGIN TRANSACTION;                     -- Starts a new transaction
    INSERT INTO table1 VALUES (1, 'a');    -- First operation
    UPDATE table2 SET col1 = 'b';         -- Second operation
    COMMIT;                               -- Commits if all operations succeed
    ```
- **COMMIT** - Saves the changes made in a transaction
    ```sql
    BEGIN TRANSACTION;
    UPDATE accounts SET balance = balance - 100;
    UPDATE accounts SET balance = balance + 100;
    COMMIT;                               -- Makes changes permanent
    ```
- **ROLLBACK** - Undoes the changes made in a transaction
    ```sql
    BEGIN TRANSACTION;
    UPDATE accounts SET balance = balance - 100;
    IF ERROR_OCCURRED THEN
        ROLLBACK;                         -- Reverts all changes if error occurs
    END IF;
    ```
- **SAVEPOINT** - Sets a savepoint within a transaction
    ```sql
    BEGIN TRANSACTION;
    INSERT INTO table1 VALUES (1);
    SAVEPOINT save1;                      -- Creates a savepoint
    INSERT INTO table1 VALUES (2);
    ROLLBACK TO save1;                    -- Rolls back to savepoint
    ```
- **SET TRANSACTION** - Sets the characteristics of the current transaction
    ```sql
    SET TRANSACTION ISOLATION LEVEL       -- Sets isolation level
    READ COMMITTED;                      -- Specifies level type
    ```
- **ISOLATION LEVEL** - Sets the isolation level for the current transaction
    ```sql
    BEGIN TRANSACTION;
    SET TRANSACTION ISOLATION LEVEL      -- Available levels:
    SERIALIZABLE;                       -- READ UNCOMMITTED
                                       -- READ COMMITTED
                                       -- REPEATABLE READ
                                       -- SERIALIZABLE
    ```

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
