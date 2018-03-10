# PostgreSQL commands 

#### Login to database
```
$ psql -U posgres
```
#### Quit
`\q`

#### Connect to database
`\c`

#### List databases
`\l`

#### List table
* Show table definitions : `\d &lt;tablename&gt;`
* List table schemas : `\dn`
* List table views : `\dv`
* List functions : `\df`
* List indexes : `\di`

#### Export a table to CSV
`\copy (SELECT * FROM __table_name__) TO 'file_path_and_name.csv' WITH CSV`: Export a table as CSV

#### Print result in pretty format 
`\x`

#### List users
`\du`

## Configuration

#### Service management commands:
```
sudo service postgresql stop
sudo service postgresql start
sudo service postgresql restart
```

#### Changing verbosity & querying Postgres log:
  <br/>1) First edit the config file, set a decent verbosity, save and restart postgres:
```
sudo vim /etc/postgresql/9.3/main/postgresql.conf

# Uncomment/Change inside:
log_min_messages = debug5
log_min_error_statement = debug5
log_min_duration_statement = -1

sudo service postgresql restart
```
  2) Now you will get tons of details of every statement, error, and even background tasks like VACUUMs
```
tail -f /var/log/postgresql/postgresql-9.3-main.log
```
  3) How to add user who executed a PG statement to log (editing `postgresql.conf`):
```
log_line_prefix = '%t %u %d %a '
```

## CRUD operations

#### Create database
`CREATE DATABASE &lt;databasename&gt;`

#### Create table
`CREATE TABLE &lt;table_name&gt`

Example:
```
CREATE TABLE COMPANY(
   ID INT PRIMARY KEY     NOT NULL,
   NAME           TEXT    NOT NULL,
   AGE            INT     NOT NULL,
   ADDRESS        CHAR(50),
   SALARY         REAL,
   JOIN_DATE	  DATE
);
```

#### Insert a record
```
INSERT INTO TABLE_NAME VALUES (value1,value2,value3,...valueN);
```

Example:
```
INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY,JOIN_DATE) VALUES (1, 'Paul', 32, 'California', 20000.00,'2001-07-13');
```

#### Delete a record
```
DELETE FROM table_name WHERE [condition];
```

Example:
```
DELETE FROM COMPANY WHERE ID = 2;
```

#### Update a reacord
```
UPDATE table_name
SET column1 = value1, column2 = value2...., columnN = valueN
WHERE [condition];
```

Example:
```
UPDATE COMPANY SET SALARY = 15000 WHERE ID = 3;
```

## Reference
``` 
- [PostgreSQL Exercises](https://pgexercises.com/): An awesome resource to learn to learn SQL, teaching you with simple examples in a great visual way. **Highly recommended**.
- [PostgreSQL Cheatsheet](https://gist.github.com/Kartones/dd3ff5ec5ea238d4c546)
