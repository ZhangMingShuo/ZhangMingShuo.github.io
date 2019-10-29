
> [!NOTE]
> TRUNCATE 
  SQL query removes all rows from a table, without logging the individual row deletions.    
  SQL 删除一张表中的所有行,没有记录单个行的删除
  TRUNCATE is a DDL command   
  TRUNCATE是DDL命令
  TRUNCATE is executed using a table lock and whole table is locked for remove all records.   
  TRUNCATE是通过表锁执行,整张表被锁定以删除所有记录.    
  We cannot use WHERE clause with TRUNCATE.   
  我们不能在TRUNCATE语句中使用WHERE子句
  TRUNCATE removes all rows from a table.
  TRUNCATE删除表的所有行
  Minimal logging in transaction log, so it is faster performance wise. 
  最小化事务日志中的日志记录，因此提高了性能。
  TRUNCATE TABLE removes the data by deallocating the data pages used to store the table data and
  records only the page deallocations in the transaction log.   
  
  Identify column is reset to its seed value if table contains any identity column.   
  To use Truncate on a table you need at least ALTER permission on the table.   
  Truncate uses less transaction space than the Delete statement.   
  Truncate cannot be used with indexed views.   
  TRUNCATE is faster than DELETE.   
