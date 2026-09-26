# XSS Mitigation Report

## Vulnerability

Cross-Site Scripting (XSS) occurs when an application processes untrusted user input and renders it in a way that allows it to be interpreted as executable content.

## Root Cause

The application does not properly encode or sanitize untrusted input before displaying it to the user.

## Mitigation

Use context-aware output encoding when displaying user-controlled data.

### Sanitized PHP

```php
$name = htmlspecialchars($name, ENT_QUOTES, 'UTF-8');
$message = htmlspecialchars($message, ENT_QUOTES, 'UTF-8');
```

This ensures that characters such as `<` and `>` are treated as text rather than HTML markup.

## Additional Protections

* Validate input on the server side.
* Avoid relying only on blacklist filtering.
* Use safe DOM APIs such as `textContent`.
* Avoid inserting untrusted data using `innerHTML`.
* Implement a restrictive Content Security Policy (CSP).
* Sanitize HTML only when HTML input is intentionally required.

## Result

User-controlled input is treated as data instead of executable HTML or JavaScript, reducing the risk of Stored, Reflected, and DOM-based XSS.

## Conclusion

Proper output encoding is the primary mitigation for XSS. Input validation and Content Security Policy provide additional layers of protection.
