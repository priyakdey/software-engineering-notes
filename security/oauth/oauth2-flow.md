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
- [Authorization Code Flow](authorization-code-flow.md)
- [Implicit Flow](#implicit-flow)
- [Resource Owner Password Credentials (ROPC)](#resource-owner-password-credentials)
- [Client Credentials](#client-credentials)


|  Query Param   | Official Term      | Who Generates        | Purpose                                           |
| :------------: | ------------------ | -------------------- | ------------------------------------------------- |
|     `code`     | Authorization Code | Authorization Server | To exchange for a access token                    |
|    `state`     | State Parameter    | Client               | Prevent CSRF + maintain client state/session like |
| `access_token` | Access Token       | Authorization Server | To provide access to necessary resource           |

## Reference:
- [The OAuth 2.0 Authorization Framework - RFC-6749](https://datatracker.ietf.org/doc/html/rfc6749#section-1.2)
- [What is OAuth really all about - OAuth tutorial - Java Brains](https://www.youtube.com/watch?v=t4-416mg6iU&list=PLqq-6Pq4lTTYTEooakHchTGglSvkZAjnE&index=13)
- [OAuth terminologies and flows explained - OAuth tutorial - Java Brains](https://www.youtube.com/watch?v=3pZ3Nh8tgTE&t=976s)