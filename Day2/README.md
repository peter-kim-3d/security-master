# Day 2 Learning Summary - November 16, 2023

## Understanding Cross-Site Request Forgery (CSRF)

### Overview
Cross-Site Request Forgery (CSRF) is a web security vulnerability that allows attackers to induce users to perform actions they do not intend to, particularly in web applications where the user is authenticated.

### How It Works
- **Authenticated User**: The victim is logged into a web application.
- **Malicious Request**: The attacker tricks the victim into making an unwanted action in the application.
- **Unintended Actions**: The application processes the request as legitimate, leading to unintended actions by the victim.

### Example Scenario
- A user is logged into a banking website.
- They visit a malicious site that sends a fraudulent request to the bank.
- The bank processes the request, thinking it's from the authenticated user.

### Prevention Techniques
1. **Anti-CSRF Tokens**: Unique tokens in forms, verified with every request.
2. **Same-Site Cookies**: Restrict cookies to same-site requests.
3. **Custom Headers**: Utilize custom headers that aren't included in cross-site requests.
4. **Check HTTP Referrer**: Verify requests originate from trusted sources.
5. **User Logout**: Encourage users to log out and implement session timeouts.

### Impact
- **On Users**: Unauthorized actions on their accounts.
- **On Web Applications**: Compromised integrity and user trust.
- **Legal Compliance**: Potential legal consequences for security lapses.

### Implementing Anti-CSRF Tokens in Java
- **Token Generation**: Create a unique token per user session.
- **Embed in Forms**: Place the token in hidden form fields.
- **Verify on Submission**: Check that the submitted token matches the session token.

### Conclusion
CSRF is a significant security threat in web applications. Implementing effective preventive measures is crucial to protect both users and the application's integrity.
