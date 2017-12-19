
INSERT语句

```mysql
INSERT INTO `table_name` (
`col_VARCHAR`,
`col_INTEGER`,
`col_null`,
`col_DATETIME`
) VALUES (
'abcdefg',
6,
null,
STR_TO_DATE('2017-12-19 11:36:04','%Y-%m-%d %H:%i:%s')
)
```
