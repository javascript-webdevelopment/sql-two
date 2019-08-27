# SQL TWO

In this lecture we go over a review of the last sql lecture and start going into table relationships.

## Schema

The `schema` is the bluepring for how our tableis structured. This is what sets the guidelines for how the data is stored inside of our database.

A schema for our table above would look similar to this

```sql
CREATE TABLE racers (
    id INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER,
    country TEXT
)
```

Above, we are determining exactly what datatypes are allowed to be inserted into each coloumn for the row that is being added to our racers table in our database.

## DataTypes

When setting up our schema we will determine what `data type` is allowed in our columns. There are many types out there, but we will cover the main ones.

### Empty Values

`Null` - This data type means an empty value.

### Numeric Values

`Integer` - This data type will define a round number.

`Decimal` - This data type can have unlimited decimal values.

`Float` - This data type can have values up to 15 decimal places.

`Serial` - This data type is an incrementing integer, usally used with primary keys to establish uniqueness.

### Character Values

`Text` - This data type declares unlimited characters in a string.

`Varchar(n)` - This data type will allow you to determine how many characters are allowed.

### Boolean Values

`Boolean` - This data type is either true or false

## Statements

SQL statements are queries that we make to our database.

A few things to note about SQL Statements:

1. We use a semicolon to delcare the end of a statement.

2. We can not have a trailing comma on our scripts. 

3. We need to use single quotes, not double.

4. It's common to use all caps, but it's not needed. It's best to stick with one way and be consistant and not use lowercase and capital characters.

### Insert Statement

We can use `insert statements` to add data into our tables. The syntax for an insert statement looks like the following.

```sql
INSERT INTO racers
(name, age, country)
VALUES
('Tayte', 22, 'US')
```

Above, we are adding myself into the database. We first delcare a insert statement with the `INSERT INTO` keyword followed by the name of the table we are inserting data into. Then in parenthesis, we select the columns to add to. We then use the `VALUES` keyword followed by another pair of parenthesis to include the data to insert into the columns.

> Note: It's import that the data lines up with the column we want to insert that data into

### Select Statement

`Select` statements are used to query our database for information. The structure for a `select` statement looks like the following.

```sql
SELECT *
FROM racers
```

Above, we delcare it's a select statement using the `SELECT` keyword. It is followed by the column name that we want to selectv data from. In this case, we used an asterik to say 'all' the data from every column. Then we declare what table to select from using the `FROM` keyword.

#### WHERE

We can use a `where clause` to add a filter to our select statements.

```sql
SELECT *
FROM racers
WHERE name = 'Tayte'
```

##### Comparison Operators

`>` - Greater than.

```sql
SELECT *
FROM racers
WHERE id > 2
```

`<` - Less than.

```sql
SELECT *
FROM racers
WHERE id < 2
```

`>=` - Greater than or equal to.

```sql
SELECT *
FROM racers
WHERE id >= 2
```

`<=` - Less than or equal to.

```sql
SELECT *
FROM racers
WHERE id <= 2
```

`!=` - Does not equate.

```sql
SELECT *
FROM racers
WHERE id != 2
```

##### Logical Operators

`AND` - Check for multiple conditions to be true.

```sql
SELECT *
FROM racers
WHERE id != 2
AND id < 3
```

`OR` - Check for only one of multiple conditions to be true.

```sql
SELECT *
FROM racers
WHERE name = 'Tayte'
OR id = 2
```

##### Null and Not Null

`IS NULL` - Checks for a value to be null.

```sql
SELECT *
FROM racers
WHERE name IS NULL
```

`IS NOT NULL` - Checks for a value NOT to be null.

```sql
SELECT *
FROM racers
WHERE name IS NOT NULL
```

##### IN Condition

`IN` - This is used as shorthand syntax to act as multiple `OR` conditions.

```sql
SELECT *
FROM racers
WHERE name IN ('Tayte', 'Samual', 'Kevin');
```

If we didn't use the `IN` key word, our statement would look like this

```sql
SELECT *
FROM racers
WHERE name = 'Tayte'
OR name = 'Samual'
OR name = 'Kevin';
```

##### BETWEEN Condition

`BETWEEN` - This is used to retrieve values in between a range.

```sql
SELECT *
FROM racers
WHERE id BETWEEN 1 AND 3;
```

#### LIMIT

The `LIMIT` clause will allow you to return a certain amount of rows from a select statement.

```sql
SELECT *
FROM racers
LIMIT 2
```

This would return the first two rows of data from the racers table.

#### ORDER BY

`ORDER BY` - This clause will sort the records in our result. This clause can only be used in select statements.

```sql
SELECT *
FROM racers
ORDER BY id
```

This will organize how result in ascending order by default.

##### ASC

`ASC` is the keyword we can use with order by to sort our records in the result in ascending order.


```sql
SELECT *
FROM racers
ORDER BY id ASC
```

##### DESC

`DESC` is the keyword we can use with order by to sort our records in the result in descending order.


```sql
SELECT *
FROM racers
ORDER BY id DESC
```

### SQL Functions

There are "functions" that we can use with PostgreSQL. This will usually handle some sort of mathematical logic for us.

`count()` - This returns the count of an expression.

```sql
SELECT count(id)
FROM racers
```

> It's important to note that count does not count null values. Pass in the `*` to account for all rows.

`min()` - This returns the minimum value of an expression.

```sql
SELECT min(age)
FROM racers
```

Above, we are finding the youngest racer.

`max()` - This returns the maximum value of an expression.

```sql
SELECT max(age)
FROM racers
```

Above, we are returning the oldest racer.

`sum()` - This returns the summed value of an expression.

```sql
SELECT sum(age)
FROM racers
```

Above, we now have the sum of the ages for all the racers.

`avg()` - This function returns the average value of an expression.

```sql
SELECT avg(age)
FROM racers
```

Above, we have found the average age of the racers.

### Update Statements

We can  update our data inside of a database by using an `update statement`.

```sql
UPDATE racers
SET name = 'Chris'
WHERE id = 2
```

Above, we have just updated the name for the user with the id of 2. We first use the `UPDATE` keyword followed by the name of the table we are updating. Then we `SET` the name to "Chris" where the user id equals 2.

### Delete Statements

We can remove or destroy data from our databased by using a `delete statement`.

```sql
DELETE FROM racers
WHERE id = 2
```

We first use the `DELETE FROM` keyword, then declare the table to remove from. We then choose the id of the racer we want to remove.

> Make sure to add the where clause or you would remove everything in the table!

## Altering Tables

We can use `alter statements` to alter our tables in our database. We generally use alter statements to modify the `schema` for our tables.

### Adding Columns

```sql
ALTER TABLE racers
ADD COLUMN team TEXT
```

### Alter Column Data Types

```sql
ALTER TABLE racers
ALTER COLUMN team
SET DATA TYPE VARCHAR(100);
```

We can also makew this shorter by using `shorthand syntax`. This way is shorter from the previous example.

```sql
ALTER TABLE racers
ALTER team
SET DATA TYPE VARCHAR(100);
```

This way is the shortest syntax we can use.

```sql
ALTER TABLE racers
ALTER team
TYPE VARCHAR(100);
```

### Renaming Columns

```sql
ALTER TABLE racers
RENAME COLUMN team
TO "group";
```

### Remove Columns

```sql
ALTER TABLE racers
DROP COLUMN group;
```

### Change Table Name

```sql
ALTER TABLE racers
RENAME TO bike_racers;
```

## Dropping A Table

We can drop our tables, if we feel the need to remove them. Be careful doing this, because we can not restore tables that have been dropped. This could lead to a lot of problems, so just keep that in mind!

```sql
DROP TABLE racers
```

## Table Relationships

A relational database is built around a model of having `relationships` between different tables to establish a way for the tables to communicate with each other.

There are a three main designs that we can establish for creating a `relationship` between tables.

### One to One

This deisgn is where one entity can only talk to one other entity. I like to think about this like a social security number. Only one person will be associated with one SSN, it will never represent more than one person.

![one to one](images/onetoone.png)

### One to Many

This design is where one entity can have multple relationships with other entities. I like to think about this like comments on a website. A comment is only owned by one person, this creates a `one to many` relationship. One user can have many comments.

![one to many](images/onetomany.png)

### Many to Many

This design is where multiple entities can have a relationship with multiple entities. I like to think about this as books and authors. A book can have many authors and an author can have many books.

![many to many](images/manytomany.png)

## Foreign Keys

Now that we have talked about some of the relational design patterns, you are probably wondering how we actually set this relationship up? This is where `foreign keys` come into play.

A `foreign key` will set a constraint to the data that is inserted into the row. The only way it data can be inserted is if a row has a column value that matches with another specific value from another table.

A `foreign key` will typically reference a `primary key` from another table.

```sql
CREATE TABLE bikes (
  id SERIAL PRIMARY KEY,
  racer_id INTEGER REFERENCES racers(id)
)
```

Above is thew syntax we would use to setup a foreign key in our schema for a table. We are saying that the `racer_id` column needs to have a matching value with a row's id from the racers table. This has now created that `relationship` between the two tables.