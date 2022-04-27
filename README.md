# SQLNotes
## MySQL - How to temporarily disable a foreign key constraint?

### To disable foreign key constraints when you want to truncate a table:

Use FOREIGN_KEY_CHECKS

`SET FOREIGN_KEY_CHECKS=0;`
  and remember to enable it when you’re done:

`SET FOREIGN_KEY_CHECKS=1;`
  Or you can use DISABLE KEYS:

`ALTER TABLE table_name DISABLE KEYS;`
  Again, remember to enable if thereafter:

`ALTER TABLE table_name ENABLE KEYS;`
  Note that DISABLE KEYS does not work on InnoDB tables as it works properly for MyISAM.

Use ON DELETE SET NULL

If you don’t want to turn key checking on and off, you can permanently modify it to `ON DELETE SET NULL`

Delete the current foreign key first:

`ALTER TABLE table_name1 DROP FOREIGN KEY fk_name1; `
`ALTER TABLE table_name2 DROP FOREIGN KEY fk_name2;`
  Then add the foreign key constraints back

`ALTER TABLE table_name1 
  ADD FOREIGN KEY (table2_id) 
        REFERENCES table2(id)
        ON DELETE SET NULL;`

`ALTER TABLE tablename2 
  ADD FOREIGN KEY (table1_id) 
        REFERENCES table1(id)
        ON DELETE SET NULL;`
