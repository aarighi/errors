## Virtualenv

On Windows: 
    mkvirtualenv-win

## Database connection

```python
    import pypyodbc
    pypyodbc.connect(‘Driver = {drivername};Server=servername; Database=databaseName; uid=username;pwd=password')
```

  - **Driver** - identifies the driver you wish to use to connect to the database, the correct driver to use will depend on which database product you are using.
  
  - **Server** - identifies the server where SQL Server is running.
  
  - **Database** - is the name of your database in SQL Server.
  
  - **uid and pwd** - are the SQL Server username and password that has permissions to log into the database and perform the desired actions.
