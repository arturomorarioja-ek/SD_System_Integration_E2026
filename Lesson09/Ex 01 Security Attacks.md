### Security Attacks

Work in groups of 4 or 5 students.

A team is building a small browser-based web application with the following features:
- Users can search products
- Users can post comments
- Logged-in users can update their profile
- Users stay logged in through a session cookie
- The application allows image upload for profile pictures
- Some pages contain important action buttons such as Delete, Confirm, or Approve

The team asks you to help decide from a software development point of view which security protections should be added before release.

For each feature below:
- Identify the primary security concern (SQL-injection, XSS, CSRF)
- Choose the two most appropriate protections
- Explain why they are appropriate

Available protections
- Parameterised database queries
- Output encoding/escaping
- CSRF token
- HTTPS
- `SameSite` cookies
- `frame-ancestors` CSP
- Request size limits
- Rate limiting
- Input validation
- Restricting allowed upload types
- Storing sessions in cookies
- Hiding buttons in the UI
- Requiring POST instead of GET
- Checking that the user is logged in

**Feature A — Relevant action buttons**  
Some pages contain actions such as Delete, Approve, or Confirm. The application may potentially be embedded inside another website.

**Feature B — Session-based login**  
Users remain logged in through a session cookie while using the application from their browser.

**Feature C — Comments**  
Users can submit comments that will later be shown to other users in the browser.

**Feature D — Image upload**  
Users can upload profile images.

**Feature E — Profile update**  
A logged-in user can change their email address from a browser form. The browser automatically sends the session cookie with the request.

**Feature F — Search**  
Users can search the product catalogue by entering free text.
