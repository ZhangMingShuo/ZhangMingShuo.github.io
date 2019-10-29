
> [!NOTE]
> TRUNCATE 
  SQL 删除一张表中的所有行,没有记录单个行的删除       
  TRUNCATE是DDL命令      
  TRUNCATE是通过表锁执行,整张表被锁定以删除所有记录.      
  我们不能在TRUNCATE语句中使用WHERE子句     
  TRUNCATE删除表的所有行     
  最小化事务日志中的日志记录，因此提高了性能。    
  TRUNCATE TABLE通过取消分配用于存储表数据的数据页面来删除数据，并仅在事务日志中记录页面的解除分配。    
  如果表包含任何标识列，则将标识列重置为其种子值。    
  至少要有ALTER权限才可以使用Truncate    
  Truncate比Delete用更少的日志空间     
  Truncate不能用来删除索引视图    
  Truncate比Delete更快

> [!NOTE]
  DELETE是DML命令。 
  使用行锁执行DELETE，表中的每一行都被锁定以进行删除。   
  我们可以使用带DELETE的where子句来过滤和删除特定记录。    
  DELETE命令用于根据WHERE条件从表中删除行。    
  DELETE语句一次删除一行，并在事务日志中为每个删除的行记录一个条目。  
  列保持的标识DELETE保留该标识。    
  要使用Delete，需要在表上具有DELETE权限。   
  Delete比Truncate使用更多的事务空间。    
  Delete可以用来删除索引视图。    
  Delete维护日志，因此比TRUNCATE慢。   
  
> [!NOTE]
> DROP删除表的所有行，索引，约束条件   
  不会有触发器被触发   
  DROP和TRUNCATE是DDL命令,而DELETE是DML命令   
  DELETE可以回滚，DROP、TRUNCATE不能    
