# The OAuth 2.0 Authorization Framework

- Stands for Open Authorization
- Used for authorizing one service to access resources on another service.

## Terminology

- **Resource**: The thing to access, usually a protected resource.
- **Resource Owner**: The actual owner (mostly human) who owns the resource. When user is human, they are referred to as end-user. The final grant of permission to a protected resource lies in the hands of the resource owner.
- **Resource Server**: The owner server which holds the resource or the server in which the resource resides
- **Client**: The client application/service which is requesting permission to the protected resource on behalf of the resource owner
- Authorization Server: The server issuing tokens and most likely validating tokens to provide access to the resource on the resource server.
## Authorization Grant

An authorization grant is a proof of consent given by the **resource owner** for the client to access the **resource**. The **client** will be using this grant to request a **access token**, which will be used for accessing the actual token.

This segregates two things:
- Consent From **Resource Owner** for **Client** to access the **Resource**.
- **Token** issuing by **Authorization Server** based on the authorization grant.

The different grant flows are below:
- [Authorization Code Flow](#authorization-code-flow)
- [Implicit Flow](#implicit-flow)
- [Resource Owner Password Credentials (ROPC)](#resource-owner-password-credentials)
- [Client Credentials](#client-credentials)
### Authorization Code Flow

- The **Client** redirects the **Resource Owner** (i.e., the user) to the **Authorization Server** to initiate the authentication and authorization process.  The Client **never handles the user’s credentials directly**. Instead, it delegates the login and consent screen to the Authorization Server.  *For example: when you click "Connect with Google", and you're redirected to `accounts.google.com` to sign in.*
- The **Authorization Server**, upon successful user authentication and consent, redirects the **User-Agent** (usually the browser) **back to the Client’s redirect URI** with two important query parameters:
	- **`code`**: The **Authorization Code** — a short-lived, one-time-use credential that the Client will later exchange for tokens.
	- **`state`**: The **State Parameter** — a value the Client originally sent in the auth request. It is echoed back to ensure the response is tied to the original request.  Its primary purpose is to **prevent CSRF attacks** and to **preserve request integrity or session information**.
- The **Client** now takes the **Authorization Code** and makes a **server-to-server POST** request to the **Authorization Server’s token endpoint** to obtain an:
	- **`access_token`**: used to call the **Resource Server** and access protected user data.


| Query Param  | Official Term      | Who Generates        | Purpose                                           |
| :----------: | ------------------ | -------------------- | ------------------------------------------------- |
|    `code`    | Authorization Code | Authorization Server | To exchange for a access token                    |
|   `state`    | State Parameter    | Client               | Prevent CSRF + maintain client state/session like |
| access_token | Access Token       | Authorization Server | To provide access to necessary resource           |

## Reference:
- [The OAuth 2.0 Authorization Framework - RFC-6749](https://datatracker.ietf.org/doc/html/rfc6749#section-1.2)
- [What is OAuth really all about - OAuth tutorial - Java Brains](https://www.youtube.com/watch?v=t4-416mg6iU&list=PLqq-6Pq4lTTYTEooakHchTGglSvkZAjnE&index=13)
- [OAuth terminologies and flows explained - OAuth tutorial - Java Brains](https://www.youtube.com/watch?v=3pZ3Nh8tgTE&t=976s)