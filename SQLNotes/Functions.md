---  
title:        Functions  
permalink:    SQLNotes/Functions  
category:     SQLNotes  
parent:       SQLNotes  
category: SQLNotes    
has_children: true    
children:     true  
layout:       default  
has_children: false  
share:        true  
shortRepo:  
  - default  
  - sqlnotes
---  
  
# MySQL  
  
## extract JSON  
  
```sql  
select JSON_EXTRACT(app_metadata, '$.tb5', '$.tb6.roleGroups') as "all",  
       JSON_EXTRACT(app_metadata, '$.tb5."roleGroups"')        as "tb5"  
from user;  
```
