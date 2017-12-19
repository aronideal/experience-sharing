
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
  `col_VARCHAR` VARCHAR(120) NOT NULL COMMENT 'VARCHAR',
  `col_TINYINT` TINYINT NOT NULL COMMENT 'TINYINT',
  `col_INT` INT COMMENT 'INTEGER',
  `col_INTEGER` INTEGER DEFAULT 66 COMMENT 'INTEGER',
  `col_null` VARCHAR(200) COMMENT 'null',
  `col_DATETIME` DATETIME NOT NULL COMMENT 'DATETIME',
  PRIMARY KEY (`id`),
  UNIQUE KEY `uk_1` (`col_INTEGER`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='table_name';
```

    其它类型：

```
  | SMALLINT[(length)] [UNSIGNED] [ZEROFILL]
  | MEDIUMINT[(length)] [UNSIGNED] [ZEROFILL]
  | BIGINT[(length)] [UNSIGNED] [ZEROFILL]
  | REAL[(length,decimals)] [UNSIGNED] [ZEROFILL]
  | DOUBLE[(length,decimals)] [UNSIGNED] [ZEROFILL]
  | FLOAT[(length,decimals)] [UNSIGNED] [ZEROFILL]
  | DECIMAL(length,decimals) [UNSIGNED] [ZEROFILL]
  | NUMERIC(length,decimals) [UNSIGNED] [ZEROFILL]
  | DATE
  | TIME
  | TIMESTAMP
  | CHAR(length) [BINARY | ASCII | UNICODE]
  | TINYBLOB
  | BLOB
  | MEDIUMBLOB
  | LONGBLOB
  | TINYTEXT
  | TEXT
  | MEDIUMTEXT
  | LONGTEXT
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
`col_TINYINT`,
`col_INT`,
`col_INTEGER`,
`col_null`,
`col_DATETIME`
) VALUES (
'idddd',
'abcdefg',
1,
6,
6,
null,
STR_TO_DATE('2017-12-19 11:36:04','%Y-%m-%d %H:%i:%s')
)
```

    默认值：

```
// DATE
NOW() 
CURRENT_DATE

// TIMESTAMP
CURRENT_TIMESTAMP
```

CREATE INDEX

```mysql
CREATE [UNIQUE|FULLTEXT|SPATIAL] INDEX index_name
    [index_type]
    ON tbl_name (index_col_name,...)
    [index_option]
    [algorithm_option | lock_option] ...

index_col_name:
    col_name [(length)] [ASC | DESC]

index_option:
    KEY_BLOCK_SIZE [=] value
  | index_type
  | WITH PARSER parser_name
  | COMMENT 'string'

index_type:
    USING {BTREE | HASH}

algorithm_option:
    ALGORITHM [=] {DEFAULT|INPLACE|COPY}

lock_option:
    LOCK [=] {DEFAULT|NONE|SHARED|EXCLUSIVE}
```



