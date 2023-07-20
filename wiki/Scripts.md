# MySQL

## disable a foreign key constraint?

> [ Modify Constraint By Adding Delete Cascade ](https://gist.github.com/14paxton/a5c69e1c4fc29bf91c0f7b626b612450)

> **Note**<br>
> `To disable foreign key constraints when you want to truncate a table`

<div style="padding: 15px; border: 1px solid transparent; border-color: transparent; margin-bottom: 20px; border-radius: 4px; color: #3c763d; background-color: #dff0d8; border-color: #d6e9c6;">
  Use FOREIGN_KEY_CHECKS
</div>

***Disable***

~~~mysql
SET FOREIGN_KEY_CHECKS = 0;
~~~

***Enable***

~~~mysql
SET FOREIGN_KEY_CHECKS = 1;
~~~

<br/>

<div style="padding: 15px; border: 1px solid transparent; border-color: transparent; margin-bottom: 20px; border-radius: 4px; color: #3c763d; background-color: #dff0d8; border-color: #d6e9c6;">
Or you can use DISABLE KEYS:
</div>

~~~mysql
ALTER TABLE table_name
    DISABLE KEYS;
~~~

~~~mysql
ALTER TABLE table_name
    ENABLE KEYS;
~~~

> **Warning**<br>
> Note that DISABLE KEYS does not work on InnoDB tables as it works properly for MyISAM.

Use

```mysql
ON
DELETE SET NULL
```

> **Warning**<br>
> If you don’t want to turn key checking on and off, you can permanently modify it to `ON DELETE SET NULL`

Delete the current foreign key first:

```mysql
ALTER TABLE table_name1
    DROP FOREIGN KEY fk_name1; 
```

```mysqlALTER

```

Then add the foreign key constraints back

```mysql
ALTER TABLE table_name1
    ADD FOREIGN KEY (table2_id)
        REFERENCES table2 (id)
        ON DELETE SET NULL;
```

```mysql
ALTER TABLE tablename2
    ADD FOREIGN KEY (table1_id)
        REFERENCES table1 (id)
        ON DELETE SET NULL;
```
