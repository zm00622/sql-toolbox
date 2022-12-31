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
