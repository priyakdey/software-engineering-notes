# Authorization Code Flow

## Flow Diagram


## Flow

- The **Client** redirects the **Resource Owner** (i.e., the user) to the **Authorization Server** to initiate the authentication and authorization process.  The Client **never handles the user’s credentials directly**. Instead, it delegates the login and consent screen to the Authorization Server.  *For example: when you click "Connect with Google", and you're redirected to `accounts.google.com` to sign in.*
- The **Authorization Server**, upon successful user authentication and consent, redirects the **User-Agent** (usually the browser) **back to the Client’s redirect URI** with two important query parameters:
	- **`code`**: The **Authorization Code** — a short-lived, one-time-use credential that the Client will later exchange for tokens.
	- **`state`**: The **State Parameter** — a value the Client originally sent in the auth request. It is echoed back to ensure the response is tied to the original request.  Its primary purpose is to **prevent CSRF attacks** and to **preserve request integrity or session information**.
- The **Client** now takes the **Authorization Code** and makes a **server-to-server POST** request to the **Authorization Server’s token endpoint** to obtain an:
	- **`access_token`**: used to call the **Resource Server** and access protected user data.

|  Query Param   | Official Term      | Who Generates        | Purpose                                           |
| :------------: | ------------------ | -------------------- | ------------------------------------------------- |
|     `code`     | Authorization Code | Authorization Server | To exchange for a access token                    |
|    `state`     | State Parameter    | Client               | Prevent CSRF + maintain client state/session like |
| `access_token` | Access Token       | Authorization Server | To provide access to necessary resource           |

## Flow Diagram
