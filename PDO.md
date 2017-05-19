# PDO
> PHP Data Object


PDO Methods:
- query - performs a SQL SELECT query on the database returning a result set as a PDOStatement object
- exec - performs a SQL query that modifies the database (insert, delete, update, etc); returns the number of affected rows
- getAttribute, setAttribute - get/set various database connection properties
- quote - encodes a value for use within a query
- prepare - prepares a statement for execution and returns a statement object


# **PDOStatement object and methods**
> PDOStatement - represents a prepared statement and, after the statement is executed, an associated result.


**PDO Syntax**:

```php
$name = new PDO("dbprogram:dbname=databse;host=server", "username", "password");
$name->query("SQL query");
```




**Methods**:
- columnCount() - number of columns in the results
- fetch() - return the next row from the results
- fetchColumn(number) - return the next column from the results
- rowCount() - number of rows returned by the query
- bindParam($parameter, $variable) - binds a parameter value to the specified variable name
- execute() - executes the prepared statement
Example:

```php
if ($rows->rowCount() > 0) {
    $first_row = $rows -> fetch();
    ...
}
```
- Using setAttribute you can tell PDO to throw PDOException when an error ocurrs

```php
$db = new PDO("mysql:dbname=university;host=localhost", "admin", "foo");
$db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$rows = $db->query("seeelect * from student"); //error example
```
- You can catch that exception

```php
try{
    $db = new PDO("mysql:dbname=university;host=localhost", "admin", "foo");
    $db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    $rows = $db->query("seeelect * from student");
    foreach($rows as row) { ... }
} catch (PDOException $ex) {
    ?>
    
    <p>Sorry, a database error ocurred. Please try again.</p>
    <p>Error details: <?= $ex->getMessage() ?></p>
    
    <?php
    ...
}
```
- exec example:

```php
$n = $db->exec("insert into students values($username, $password, $course)");
```






