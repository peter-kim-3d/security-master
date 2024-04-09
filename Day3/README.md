# Day 3 Learning Summary - April 9, 2024

## SQL Injection (SQLi)

### Overview
SQL Injection (SQLi) is a security vulnerability that enables attackers to interfere with the queries an application makes to its database. It's known for its prevalence and potential to cause significant harm to web applications.

### How It Works
- **Vulnerable Input**: Attackers provide malicious SQL code as input to a web application, exploiting unvalidated input fields.
- **Malicious Execution**: The malicious input manipulates backend SQL queries, leading to unintended database actions.
- **Compromised Database**: This vulnerability can result in unauthorized access, data modification, and in severe cases, control over the database server.

### Example Scenario
- An application constructs SQL queries using unsanitized user input.
- An attacker inputs a malicious string, altering the intended SQL query to gain unauthorized access or manipulate data.

### Prevention Techniques
1. **Prepared Statements (Parameterized Queries)**: These ensure SQL commands execute as intended, preventing attackers from altering the query.
2. **Stored Procedures**: They encapsulate the SQL logic on the database side, adding a security layer.
3. **White List Input Validation**: Accept only pre-approved input.
4. **Escaping All User Supplied Input**: While not foolproof, escaping inputs can serve as an additional defense mechanism.
5. **Regular Updates and Patches**: Keeping software up-to-date to mitigate known vulnerabilities.

### Impact
- **Data Breach**: Unauthorized disclosure of sensitive information.
- **Data Loss**: Potential loss or corruption of data.
- **Reputation Damage**: Loss of trust and confidence from users or clients.
- **Legal Consequences**: Fines and legal action due to failure in protecting user data.

### Implementing Prevention in Java
Prepared statements with parameterized queries are highly effective against SQLi. Here's a simple Java example using JDBC:

```java
String safeSQLQuery = "SELECT * FROM users WHERE user_id = ?";
try (Connection connection = dataSource.getConnection();
     PreparedStatement preparedStatement = connection.prepareStatement(safeSQLQuery)) {
    preparedStatement.setInt(1, userId);
    ResultSet resultSet = preparedStatement.executeQuery();
    while (resultSet.next()) {
        // Processing the result...
    }
}
