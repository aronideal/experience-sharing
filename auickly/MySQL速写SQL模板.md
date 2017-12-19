
CREATE DATABASE

```mysql
CREATE DATABASE `database_name` DEFAULT CHARACTER SET utf8;
```

USE

```mysql
USE `study`;
```

DROP TABLE

```mysql
DROP TABLE IF EXISTS `table_name`;
```

CREATE TABLE

```mysql
CREATE TABLE `table_name` (
  `id` VARCHAR(36) NOT NULL COMMENT 'ID',
  `col_VARCHAR` VARCHAR(120) NOT NULL COMMENT 'col_VARCHAR',
  `col_INTEGER` INTEGER COMMENT 'col_INTEGER',
  `col_null` VARCHAR(200) COMMENT 'col_null',
  `col_DATETIME` DATETIME NOT NULL COMMENT 'col_DATETIME',
  PRIMARY KEY (`id`),
  UNIQUE KEY `uk_1` (`col_INTEGER`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='table_name';
```

FOREIGN KEY

```mysql
CREATE TABLE `table_name`
(
  `super_id` VARCHAR(36) NOT NULL COMMENT '引用table_super_name表',
  FOREIGN KEY (`super_id`) REFERENCES `table_super_name` (`id`)
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
