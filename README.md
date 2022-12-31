# sql-toolbox

SQL query to search for WordPress media assets:

```

Select * from wp_posts where post_type = 'attachment';

```

Location of DB Engine Install (Where MySQL currently resides on file system):

```
/Users/Shared/DBngin/mysql

```
<hr>

# MySQL Password and Username Reset for the following errors:

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' 

```

```
Access Denied for User 'root'@'localhost' (using password: YES/NO)

```

```
  code: 'ER_ACCESS_DENIED_ERROR',
  errno: 1045,
  sqlMessage: "Access denied for user 'root'@'localhost' (using password: YES)",
  sqlState: '28000',
  
```

Step 1. Navigate to "support-files" in:

```
/Users/Shared/DBngin/mysql

```

Step 2. Once there, use the following command to start mysql server:

```
mysql.server start --skip-grant-tables

```

Step 3. Once the server successfully starts, then navigate back to the bin folder. Type "mysql" into the command line and press enter to launch the mysql command prompt:

```
mysql

```

Step 4. Enter the following command to flush the privileges:

```
FLUSH PRIVILEGES;

```

Step 5. Insert new password:

```
ALTER USER 'root'@'localhost' IDENTIFIED BY 'password';

```

Step 6. To shut down the mysql server that was started from your terminal, run the following command from the bin directory:

```
mysql.server stop

```

Step 7. To start again, run:

```
mysql.server start

```

Then run:

```
mysql -u root -p

```

<hr>

If the above steps don't work, then try:


Create new user from the bin folder (instead of using root) fixed my problem.

```

mysql> CREATE USER 'test_user'@'%' IDENTIFIED BY 'password';
Query OK, 0 rows affected (0.00 sec)

```

Then grant:

```

mysql> GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, RELOAD, PROCESS, REFERENCES, INDEX, ALTER, SHOW DATABASES, CREATE TEMPORARY TABLES, LOCK TABLES, EXECUTE, REPLICATION SLAVE, REPLICATION CLIENT, CREATE VIEW, SHOW VIEW, CREATE ROUTINE, ALTER ROUTINE, CREATE USER, EVENT, TRIGGER ON *.* TO 'test_user'@'%' WITH GRANT OPTION;

```

Then change the credentials in your env or javascript file:

```

  var connection = mysql.createConnection({
    host     : 'The mysql IP',
    port     : 'The mysql Port',
    user     : 'new_iser',
    password : 'new_user_pass',
    database : 'database-name'
  }); 

```
