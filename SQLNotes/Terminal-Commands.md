# MYSQL 

mysql -u USERNAME -p 

show databases; 

## SETTING TIMEZONES 

Get timezone = SELECT @@global.time_zone, @@session.time_zone; 

Get timestamp = SELECT CURRENT_TIMESTAMP(); 

Set timestamp utc = SET @@session.time_zone='+00:00'; 

You can set in my.cnf 

[mysqld] 

## other variables** 

default_time_zone='+00:00' 

-GET PATHS 
```bash
SHOW VARIABLES WHERE Variable_Name LIKE "%dir"
```

 

## MySQL import 

```bash
LOAD DATA LOCAL INFILE 'C:/Groovy/englishData.csv' INTO TABLE original_data 

FIELDS TERMINATED BY ','  

ENCLOSED BY '"'  

LINES TERMINATED BY '\r\n' 
```

## Show db users
```bash
SELECT user,authentication_string,plugin,host FROM mysql.user;
```
