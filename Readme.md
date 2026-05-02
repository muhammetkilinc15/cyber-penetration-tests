## Cyber Penetration Tests

This repository is a collection of penetration tests performed on the OWASP Juice Shop web application. Each test is documented with a description of the challenge, the steps taken to complete it, and the results observed. The tests cover various vulnerabilities and attack vectors, providing insights into common security issues in web applications and how to exploit them for educational purposes.

### Purpose

The main goal of this repository is to learn penetration testing in a hands-on way and to understand web application security from both sides of the table. By practicing real attacks on a deliberately vulnerable application like OWASP Juice Shop, the aim is to:

- Build a practical understanding of common web vulnerabilities (XSS, SQL injection, broken access control, unvalidated redirects, improper error handling, missing input validation, etc.).
- See how an attacker actually thinks and what kind of mistakes in the code they look for.
- Bring that attacker's perspective back into day-to-day development, so that future code is written more carefully — with proper input validation, output encoding, parameterized queries, safe error handling, and least-privilege defaults.
- Get familiar with browser developer tools, network inspection, and basic exploitation techniques as part of a normal developer's toolkit.

In short: the point is not to break things, but to understand _why_ they break, so that the code we write afterwards is harder to break.

### Table of Contents

| #   | Challenge                                                            | Category                  | Short Description                                                                       |
| --- | -------------------------------------------------------------------- | ------------------------- | --------------------------------------------------------------------------------------- |
| 1   | [Score Board](1-score-board.md)                                      | Information Disclosure    | Find the hidden score board page by inspecting the application's source code.          |
| 2   | [DOM XSS](2-dom-xss.md)                                              | Cross-Site Scripting      | Inject a malicious iframe into the search box to trigger a JavaScript alert.            |
| 3   | [Bonus Payload](3-bonus-payload.md)                                  | Cross-Site Scripting      | Extend the DOM XSS attack to embed an external Soundcloud player via iframe.            |
| 4   | [Privacy Policy](4-privacy-policy.md)                                | User Flow                 | Register, log in, and read the application's privacy policy.                            |
| 5   | [Bully Chatbot](5-bully-chatbot.md)                                  | Business Logic            | Pressure the support chatbot until it hands out a discount coupon code.                 |
| 6   | [Error Handling](6-error-handling.md)                                | Improper Error Handling   | Provoke unhandled errors that leak server version and SQL details.                      |
| 7   | [Missing Encoding](7-missing-encoding.md)                            | Improper Input Handling   | Fix a broken image URL by manually encoding the `#` character as `%23`.                 |
| 8   | [Outdated Allowlist](8-unvalidated-redirects.md)                     | Unvalidated Redirects     | Find legacy crypto wallet links still allowed by the redirect allowlist.                |
| 9   | [Zero Stars](9-zero-star-input-validation.md)                        | Input Validation          | Bypass client-side validation to submit a zero-star feedback via DOM tampering.         |
| 10  | [Login Admin](10-login-admin-sql-injection-1.md)                     | SQL Injection             | Log in as admin by injecting `' OR TRUE --` into the email field.                       |
| 11  | [Admin Section](11-admin-section-security-misconfiguration.md)       | Security Misconfiguration | Discover and access the hidden `/administration` route as an admin user.                |
| 12  | [Password Strength](12-password-strength-broken-authentication.md)   | Broken Authentication     | Crack the admin's weak password (`admin123`) using brute-force / dictionary attacks.    |

### Conclusion

Going through these challenges shows that most vulnerabilities are not exotic — they come from small, everyday coding decisions: trusting user input, leaking information through error messages, forgetting to encode output, or leaving outdated configuration in place. Looking at an application from the attacker's point of view makes these mistakes much easier to spot in your own code before they reach production. The takeaway is simple: secure software is not a separate phase added at the end, it is the result of writing each line with the awareness that someone, somewhere, will try to misuse it.

### Disclaimer

All tests documented here were performed on a local instance of OWASP Juice Shop, which is an intentionally vulnerable application designed for learning. This material is for educational purposes only. Do not use any of the techniques shown here against systems you do not own or do not have explicit permission to test.
