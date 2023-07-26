# MySQL

## extract JSON

```sql
select JSON_EXTRACT(app_metadata, '$.tb5', '$.tb6.roleGroups') as "all",
       JSON_EXTRACT(app_metadata, '$.tb5."roleGroups"')        as "tb5"
from user;
```
