# PostgreSQL

### Resources

https://www.postgresqltutorial.com/

https://www.postgresql.org/docs/current/tutorial.html

https://www.enterprisedb.com/postgres-tutorials/postgresql-replication-and-automatic-failover-tutorial

### Background

- Open Source Relational Database Management System (RDBMS).
- Support for all platforms (Windows, Linux, Mac).
- Widely used, documented and supported.
- Strong reputation for reliability, scalability, extensibility, and data integrity.
- Industry standard for Rails.


### Commands

https://www.postgresqltutorial.com/psql-commands/

- Tip - **Commands must always end in a semi-colon `;`**

|Command|Options|Description|Example|
|:-:|:-:|:-:|:-:|
|psql (in terminal)|--help <br> -l <br> -d 'database' <br> -U 'user' <br> -h 'host' <br> -W | show help <br> list databases <br> connect to database <br> connect to user <br> force password prompt|psql -d recipes_development -U garveychan -W|
|\l|none|list all available databases|\l|
|\c <br> \connect|'database_name'|connect to another database|\c recipes_development|
|\d|'table_name'|describe a table|\d recipes|
|\dt|none|list all available tables|\dt|
|\dn|none|list all schemas|\dn|
|\ds|none|list all sequences|\ds|
|\df|none|list all functions|\df|
|\dv|none|list all views|\dv|
|\du|none|list all users and their roles|\du|
|\g|none|rerun the previous command|\g|
|\s|none <br> 'file_name'|show command history <br> save command history to file|\s command_history.txt|
|\i|'file_name'|execute commands from file|\i ~/sql/create_table.sql|
|\\?|none|show general help|\\?|
|\h|none|show available commands/help|\h|
|\q|none|exit|\q|

### Creating Tables

By default, `CREATE TABLE` creates a table in the connected database and in the public schema. The case of the command doesn't matter. Column definitions are separated by commas. Constraints can be added after the column definitions:
- Primary key
- Not null
- Unique
- Foreign keys

Example -
```
create table if not exists categories(
  id serial primary key,
  name varchar(100) not null,
  description varchar(1000)
  min_price numeric not null
);
```

This creates a table called **categories** if it doesn't already exist.
Its attributes/columns are **id, name, and description**.
The attribute **id** is a **serial** which is an intger that **auto-increments** with each new **record**.
The attributes **name** and **varchar** are **varchars** or **strings** with character lengths of **100 and 1000** respectively.
**ID** is the primary key for this table and **name** / **min_price** can't be **null**.
**Min_price** is a **numeric** value.

##### Column Properties

|Property|Description|
|:-:|:-:|
|Name|name of the column|
|Data Type|the postgreSQL data type|
|Length and Precision|length or precision of the data - for strings or numerics respectively|
|Not Null|if true, this column must be populated|
|Primary Key|if true, this column forms part of the primary key|
|Foreign Key|references a column in another table|

##### Data Types

https://www.postgresqltutorial.com/postgresql-data-types/

##### Naming Conventions

It can be helpful to name tables with the same convention as Rails.

- Table names would be **snake_case** and **plural**.
- Column names would be **snake_case** and **singular**.

### Altering Tables

`ALTER TABLE` can be used to adjust an existing table to make changes such as:
- **Add** a column
- **Drop** a column
- Change the **data type** of a column
- **Rename** a column
- Set a **default** value for the column
- Add a **constraint** to a column
- **Rename** a table

https://www.postgresqltutorial.com/postgresql-alter-table/

##### Selecting Records

https://www.postgresqltutorial.com/postgresql-select/

`SELECT * FROM table_name;`
- lists all the records from the specified table.

`SELECT attribute_1, attribute_2 FROM table_name;`
- lists records under attribute_1 and attribute_2 from the specified table.

`SELECT * from table_name where attribute_1 = value;`
- lists all records where attribute_1 is equal to value.

**Useful functions:**
- [DISTINCT](https://www.postgresqltutorial.com/postgresql-select-distinct/) operator - selecting unique rows
- [ORDER BY](https://www.postgresqltutorial.com/postgresql-order-by/) clause - sort returned rows
- [WHERE](https://www.postgresqltutorial.com/postgresql-where/) clause - filter returned rows
- [FETCH](https://www.postgresqltutorial.com/postgresql-fetch/) / [LIMIT](https://www.postgresqltutorial.com/postgresql-limit/) - select a subset of rows from a table

Examples
```
-- Put your select statements below each problem below.

-- 1. Select all items
select * from items;

-- 2. Select the category id for 'toys'
select id from categories where name = 'toys';

-- 3. Select all names of items for the 'toys' category
select name from items where category_id = 1;

-- 4. Select the items with prices greater than $10.00 
select * from items where price > 10;

-- 5. Select the category id for 'crafts'
select id from categories where name = 'crafts';

-- 6. Select the names and prices for all items in the toys and crafts categories
select name, price from items where category_id = 1 or category_id = 2;
```

##### Inserting Records

`INSERT INTO table_name (COLUMNS) VALUES;`
- specify column names in **any order** and match order of values
- will return an error if values are missing for primary keys or not null constraints

Examples
```
insert into categories (name, description)
values
  ('toys', 'Playthings'),
  ('crafts', 'Craft supplies'),
  ('clothes', 'Beautiful things to wear'),
  ('electronics', 'Gadgets for living');
```
```
insert into products(name, description, category, price)
	values
		(
			'Pokemon stickers',
			'Random collection of cool Pokemon stickers',
			null,
			19.99
		),
		(
			'Mighty Mouse',
			'The coolest mouse you''ll ever own.',
			'Accessories',
			29.89
		);
```
- Tips 
  - Notice that **null** has been used in the first entry to skip the category. This will throw an error if that attribute has a **null constraint**.
  - Notice that the single quote in the second record in `you''ll` has been **escaped** using another single quote.
