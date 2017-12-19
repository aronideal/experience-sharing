
CREATE DATABASE

```mysql
CREATE DATABASE `database_name` DEFAULT CHARACTER SET utf8;
```

DROP TABLE

```mysql
DROP TABLE IF EXISTS `table_name`;
```

CREATE TABLE

```mysql
CREATE TABLE `table_name` (
  `id` varchar(36) NOT NULL COMMENT 'ID',
  `col_VARCHAR` varchar(120) NOT NULL COMMENT 'col_VARCHAR',
  `col_INTEGER` integer COMMENT 'col_INTEGER',
  `col_null` varchar(200) COMMENT 'col_null',
  `col_DATETIME` datetime NOT NULL COMMENT 'col_DATETIME',
  PRIMARY KEY (`id`),
  UNIQUE KEY `uk_1` (`col_INTEGER`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='table_name';
```

INSERT

```mysql
INSERT INTO `table_name` (
`id`,
`col_VARCHAR`,
`col_INTEGER`,
`col_null`,
`col_DATETIME`
) VALUES (
'idddd',
'abcdefg',
6,
null,
STR_TO_DATE('2017-12-19 11:36:04','%Y-%m-%d %H:%i:%s')
)
```
