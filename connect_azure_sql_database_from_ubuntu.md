# Connect Azure SQL Database From Ubuntu

### 配置 TDS Driver

```zsh
$ sudo apt-get install -y freetds-dev freetds-bin
```

`freetds`会从以下两个文件中读取配置信息，优先读取第一个位置

- `$HOME/.freetds.conf`
- `/etc/freetds/freetds.conf`

Example:

```zsh
# freetds.conf
[global]
    tds version = 7.1
    
[<SERVERNAME>]
    host = <HOST>.database.chinacloudapi.cn
    port = 1433
```

测试能否成功连接:

```zsh
$ tsql -S <SERVERNAME> -D <DBNAME> -U <USER>@<HOST> -P <PASSWORD>
```

### 配置ODBC Driver

```zsh
$ sudo apt-get -y install tdsodbc unixodbc
```

配置`driver`:

```zsh
# /etc/odbcinst.ini
[FreeTDS]
Description = FreeTDS Driver
Driver = /usr/lib/x86_64-linux-gnu/odbc/libtdsodbc.so
```

配置 data source names (`DSN`):

```zsh
# /etc/odbc.ini
[<DSN>]
Driver = FreeTDS
Servername = <SERVERNAME> # from freetds.conf
Port = 1433
Database = <DBNAME>
```

测试是否能够连上数据库:

```zsh
$ isql -v <DSN> <USER>@<HOST> <PASSWORD>
```

### 从python中连接数据库

再装好前面的`freetds driver`和`odbc driver`之后，还需要安装`pyodbc`

```zsh
$ pip install pyodbc
```

之后就可以在python中连接`SQL Server`

```python
import pyodbc

connection = pyodbc.connect('DSN=<DSN>;UID=<USERNAME>@<HOST>;PWD=<PASSWORD>')

RANDOM_NUMBER_SQL = '''
select
round(((100 - 1 - 1) * rand() + 1), 0) as [random_number]
'''

cursor = connection.cursor()

for row in cursor.execute(RANDOM_NUMBER_SQL):
    print 'random_number = {random_number:.0f}'.format(random_number=row.random_number) 
```

### References

- [How To Connect Azure SQL Database From Ubuntu](https://bitbucket.org/janihur/devoops/wiki/How%20To%20Connect%20Azure%20SQL%20Database%20From%20Ubuntu)
- [Connecting MS SQL using freetds and unixodbc: isql - no default driver specified](https://askubuntu.com/questions/167491/connecting-ms-sql-using-freetds-and-unixodbc-isql-no-default-driver-specified)