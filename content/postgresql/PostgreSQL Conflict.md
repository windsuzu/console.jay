---
draft: false
date: 2024-05-18 17:48
tags:
  - postgres
---



```sql
ON CONFLICT (id) DO NOTHING;
ON CONFLICT (id) DO UPDATE SET email = EXCLUDED.email;
ON CONFLICT (id) DO UPDATE SET email = EXCLUDED.email, gender = EXCLUDED.gender;
```




> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners (youtube.com)](https://www.youtube.com/watch?v=qw--VYLpxG4) 
