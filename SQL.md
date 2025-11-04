## Schemas
The schema is a collection of rules that the database will enforce on the tables that are part of the schema. It can be used to group tables together and define specific user permission on each group. THe default schema is called `dbo`.

```sql
CREATE SCHEMA [<name>|AUTHORIZATION <user>]
[<list_tables>];

// RESTRICT only drops if empty, CASCADE forces drop
DROP SCHEMA <name> {RESTRICT|CASCADE}; 
```

## Domains
A domain is a user created data type. It has to come from a built-in data type and can have additional restrictions. The user who creates the domain becomes its owner.

### Creation
```sql
CREATE DOMAIN <name> [AS] <data_type>
	[<default_value>] [<restrictions>]

// restrictions definition
[CONSTRAINT <name>] CHECK (<conditions>)	
```

Example: an age domain where you have to be an adult.
```sql
CREATE DOMAIN AGE AS YEAR
	CHECK (VALUE > 18 AND VALUE , 120)
```

### Drop
```sql
// RESTRICT only drops if not used, CASCADE forces drop
DROP DOMAIN <name> {RESTRICT|CASCADE} 
```
## Tables
### Creation
```sql
CREATE TABLE <name>
(
	<column_definition>,
	[<column_definition>,..]
	[<restrictions>]
);

// column definition
<column_name> {<data_type>|<domain>} [<default_value>] [<restrictions>]
```

Column data types
![[Pasted image 20251022085834.png]]
### Drop
### Alter