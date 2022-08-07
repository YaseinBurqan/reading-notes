# Authentication

## Securing Passwords with Bcrypt Hashing Function

The benefit of hashing is that if someone steals the database with hashed passwords, they only make off with the hashes and not the actual plaintext passwords.

There are some weaknesses in cryptographic hash algorithm that allows an attacker to calculate the original value of a hashed password, as explained below: Brute Force attack: Hashes can't be reversed, so instead of reversing the hash of the password, an attacker can simply keep trying different inputs until he does not find the right now that generates the same hash value, called brute force attack.

Hash Collision attack: Hash functions have infinite input length and a predefined output length, so there is inevitably going to be the possibility of two different inputs that produce the same output hash.

This work factor value determines how slow the hash function will be, means different work factor will generate different hash values in different time span, which makes it extremely resistant to brute force attacks.

This method of hashing passwords is solid enough for most web applications that stores users' passwords and other sensitive data.

## Basic access authentication

In the context of an HTTP transaction, basic access authentication is a method for an HTTP user agent (e.g.

In basic HTTP authentication, a request contains a header field in the form of Authorization: Basic , where credentials is the Base64 encoding of ID and password joined by a single colon :.

HTTP Basic authentication (BA) implementation is the simplest technique for enforcing access controls to web resources because it does not require cookies, session identifiers, or login pages; rather, HTTP Basic authentication uses standard fields in the HTTP header.

Because the BA field has to be sent in the header of each HTTP request, the web browser needs to cache credentials for a reasonable period of time to avoid constantly prompting the user for their username and password.

HTTP does not provide a method for a web server to instruct the client to "log out" the user.

    <script>document.execCommand('ClearAuthenticationCache');</script>

In modern browsers, cached credentials for basic authentication are typically cleared when clearing browsing history.

Most browsers allow users to specifically clear only credentials, though the option may be hard to find, and typically clears credentials for all visited sites.When the server wants the user agent to authenticate itself towards the server after receiving an unauthenticated request, it must send a response with a HTTP 401 Unauthorized status line[ and a WWW-Authenticate header field. The WWW-Authenticate header field for basic authentication is constructed as following: When the user agent wants to send authentication credentials to the server, it may use the Authorization header field.

## Authentication Cheat Sheet

Authentication is the process of verifying that an individual, entity or website is whom it claims to be. Authentication in the context of web applications is commonly performed by submitting a username or ID and one or more items of private information that only a given user should know. Session Management is a process by which a server maintains the state of an entity interacting with it. Sessions should be unique per user and computationally very difficult to predict. Make sure your usernames/user IDs are case-insensitive. Usernames should also be unique. For high-security applications, usernames could be assigned and secret instead of user-defined public data.

### Authentication Solution and Sensitive Accounts¶

- Do NOT allow login with sensitive accounts (i.e. accounts that can be used internally within the solution such as to a back-end / middle-ware / DB) to any front-end user-interface

- Do NOT use the same authentication solution (e.g. IDP / AD) used internally for unsecured access (e.g. public access / DMZ)

### Implement Proper Password Strength Controls¶

A "strong" password policy makes it difficult or even improbable for one to guess the password through either manual or automated means.

- Password Length

###

    Maximum password length should not be set too low, as it will prevent users from creating passphrases. It is important to set a maximum password length to prevent long password Denial of Service attacks.

### Implement Proper Password Strength Controls

Authentication General Guidelines

    Usernames/user IDs are case-insensitive. Maximum password length is 64 characters due to limitations in certain hashing algorithms. Do NOT use the same authentication solution (e.g. IDP / AD) used for unsecured access internally for sensitive accounts. It is critical for an application to store a password using the right cryptographic technique. Compare Password Hashes Using Safe Functions.

    Where possible, the user-supplied password should be compared to the stored password hash. This is to ensure that it's the legitimate user who is changing the password.

### Example using pseudo-code for a login feature

First implementation using the "quick exit" approach

- If the user doesn't exist and the password doesn't match, the application will throw an error. In return, the response time will be different for the same error. This allows an attacker to differentiate between a wrong username and a wrong password.

<br/>

    IF USER_EXISTS(username) THEN
    password_hash=HASH(password)
    IS_VALID=LOOKUP_CREDENTIALS_IN_STORE(username, password_hash)
    IF NOT IS_VALID THEN
        RETURN Error("Invalid Username or Password!")
    ENDIF
    ELSE
    RETURN Error("Invalid Username or Password!")
    ENDIF

Second implementation without relying on the "quick exit" approach:

- This code will go through the same process no matter what the user or password is, it will return a generic error message can be determined based on the criticality of the application and its data and allowing the application to return in approximately the same response time. For critical applications, a user will always be redirected to the support page and a generic error message will be returned.

- A legitimate user might feel confused with the generic messages, thus making it hard for them to use the application, and might after several retries, leave the application because of its complexity.

<br/>

    password_hash=HASH(password)
    IS_VALID=LOOKUP_CREDENTIALS_IN_STORE(username, password_hash)
    IF NOT IS_VALID THEN
    RETURN Error("Invalid Username or Password!")
    ENDIF

Incorrect response examples:

- "Login for User foo: invalid password."
- "Login failed, invalid user ID."
- "Login failed; account disabled."
- "Login failed; this user is not active."

Correct response example:

- "Login failed; Invalid user ID or password."

Incorrect response examples:

- "We just sent you a password reset link."
- "This email address doesn't exist in our database."

Correct response example:

- "If that email address is in our database, we will send you an email to reset your password."

Incorrect response examples:

- "This user ID is already in use."
- "Welcome! You have signed up successfully."

Correct response example:

- "A link to activate your account has been emailed to the address provided."

    There are a number of different types of automated attacks that attackers can use to try and compromise user accounts. Different protection mechanisms can be implemented to protect against these attacks. This section will focus primarily on preventing brute-force attacks, although these controls can also be effective against other types of attacks. The counter of failed logins should be associated with the account itself, rather than the source IP address. Care must be taken to prevent it being used to cause a denial of service by locking other users out.

<br/>

[npm - bcrypt docs](https://www.npmjs.com/package/bcrypt)
