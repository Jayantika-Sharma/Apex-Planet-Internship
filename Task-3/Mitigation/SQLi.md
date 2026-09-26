# SQL Injection Mitigation Report

## Vulnerability

SQL Injection occurs when untrusted user input is incorporated into SQL queries without properly separating data from SQL commands.

## Root Cause

The application directly concatenates user-controlled input into SQL statements.

### Vulnerable PHP

```php
$query = "SELECT * FROM users WHERE id = '$id'";
```

## Mitigation

Use prepared statements and parameterized queries.

### Sanitized PHP

```php
$stmt = $pdo->prepare(
    "SELECT * FROM users WHERE id = :id"
);

$stmt->execute([
    ':id' => $id
]);
```

The parameter is treated as data rather than SQL syntax.

## Additional Protections

* Use prepared statements throughout the application.
* Validate input according to its expected type.
* Apply least-privilege permissions to database accounts.
* Avoid dynamically constructed SQL queries.
* Do not expose detailed database errors to users.
* Keep database software and dependencies updated.

## Result

User input is separated from the SQL query structure, preventing it from being interpreted as SQL commands.

## Conclusion

Parameterized queries are the primary defense against SQL Injection. Input validation, least-privilege database accounts, and secure error handling provide additional protection.
