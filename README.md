### Recommended to create a class or a json file to storage all important information
### Note: database name is required if trying to query data from a database

## Example
``` python
class info:
    user='root'
    password='yourPassword'
    host='localhost'
    database='databaseName'
```

# Initialize module
``` python
db = MysqlPlus(info.user,info.password,info.host)
```

# Show databases
``` python
dbs = db.show_databases()
print(dbs)
```

# Create database
``` python
db.create_database('databaseName')
```

# Drop (delete) database
``` python
db.drop_database('databaseName')
```

# Show tables
``` python
tables = db.show_tables()
print(tables)
```

# Create table
Make sure to use mysql data types when creating tables
id it is set to auto increment, do not use id as a table row
``` python
#   **kwarg Example
db.create_table('tableName',
    name='VARCHAR(10)',
    last_name='VARCHAR(20)',
    age='INT'
)
db.create_table('tableName',**kwarg)
```

# Drop (delete) table
``` python
db.drop_table('tableName')
```

# Insert into table
``` python
#   **kwarg Example
db.insert(
    name='Elon',
    last_name='Musk',
    age=50
)
db.insert('tableName',**kwarg)
```

# Fetch one result from table
``` python
#whereSql example: name='juan' AND age > 21
db.fetch_one('tableName',whereSql:str)
```

# Fetch all result from table
``` python
#whereSql example: name='juan' AND age > 21
# Also you can limit result using sql name='juan' AND age > 21 LIMIT 10
db.fetch_all('tableName',whereSql:str)
```

# Update 
``` python
# setSql example: name='Tesla', ceo='Elon musk'
# setSql example2: name='Tesla'
# whereSql example: name='tesla' AND date > '2021-10-10'
# whereSql example2: name='tesla'
db.update('tableName',setSql:str,whereSql:str)
```

# Delete 
It will delete all the records where name is equal to tesla
``` python
# whereSql example2: name='tesla'
db.update('tableName',whereSql:str)
```

# Run open sql 
Run any sql code
set commit=True if making any changes like updating record
``` python
sql = "SHOW DATABASES"
db.sql(sql)
```