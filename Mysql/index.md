# mysql

## 模糊查询

user_name 普通索引

>  索引无效

	where user_name like '%西%'

	where user_name like '%西'


>  索引有效

	where user_name like '西%'