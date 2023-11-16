# Day 1 Learning Summary - November 15, 2023

## Content Security Policy (CSP)
- **Overview**: CSP is a security standard used to prevent attacks like Cross Site Scripting (XSS) and data injection.
- **Function**: Restricts web browsers from executing unauthorized scripts.
- **Implementation**: Through directives in HTTP headers or meta tags.
- **Key Aspects**: Includes directives for resource types and sources, and supports violation reports.
- **Challenges & Best Practices**: Requires careful management and regular updates.

### Implementing CSP in Java Servers
- **Method**: Set `Content-Security-Policy` in servlet filters.
- **Example**:
  response.setHeader("Content-Security-Policy", "default-src 'self'; script-src 'self'; object-src 'none';");

## Impact of CSP on Users
- **Web Users**: Can affect loading of resources, inline scripts, and functionalities depending on the policy.
- **API Consumers**: Limited direct impact, but can affect browser-based interfaces for APIs.

## HTTP Strict Transport Security (HSTS)
- **Purpose**: Enforces secure HTTPS connections to protect against attacks like protocol downgrade.
- **Key Components**: Includes `max-age`, `includeSubDomains`, and optional `preload` directive.

### Implementing HSTS in Java Servers
- **Method**: Set `Strict-Transport-Security` in servlet filters.
- **Example**:
  response.setHeader("Strict-Transport-Security", "max-age=63072000; includeSubDomains");

## X-Content-Type-Options
- **Purpose**: Prevents MIME type sniffing by browsers.
- **Directive**: `nosniff` - ensures strict adherence to declared MIME types.
- **Security Benefit**: Mitigates risks like XSS attacks by enforcing correct MIME types.

### Implementing `X-Content-Type-Options` in Java Servers
- **Method**: Set `X-Content-Type-Options` in servlet filters.
- **Example**:
  response.setHeader("X-Content-Type-Options", "nosniff");
