# Read Me File

# Bearer Authorization

## What is JSON Web Token?

    The JWT is an open standard for securely transmitting information between parties. It can be digitally signed using a secret or public/private key pair using RSA or ECDSA. The signature also certifies that only the party holding the private key is the one that signed it.

## When should you use JSON Web Tokens?

- Authorization
- Information Exchange

    JWTs are a good way of securely transmitting information between parties. Because they can be signed, you can be sure the senders are who they say they are. The signature is calculated using the header and payload, so you can also verify that the content hasn't been tampered with.

## What is the JSON Web Token structure?

In its compact form, JSON Web Tokens consist of three parts separated by dots (.), which are:

    - Header
    - Payload
    - Signature

Header : The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.

Payload : The second part of the token is the payload, which contains the claims. Claims are statements about an entity (typically, the user) and additional data. There are three types of claims: registered, public, and private claims.

Signature : To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.

## How do JSON Web Tokens work?

In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. The server's protected routes will check for a valid JWT in the Authorization header. If it's present, the user will be allowed to access protected resources.

## Why should we use JSON Web Tokens?

Security-wise, SWT can only be symmetrically signed by a shared secret using the HMAC algorithm. JWT and SAML tokens can use a public/private key pair in the form of a X.509 certificate for signing. This highlights the ease of client-side processing of the JWT on multiple platforms, especially mobile.

## Things I want to know more about
