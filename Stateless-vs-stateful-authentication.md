# Stateless vs stateful authentication

## stateful authentication (session based auth.)
Stateful session is created on the backend side, and the corespondent session reference Id is sent to the client. Each time the client makes a request to the server, the server locates the session memory using the reference Id from the client and finds the authentication information.
In this model, you can easily imagine that if the session memory is deleted on the backend side, then the session reference Id, which the client is holding, is completely meaningless.

- user submits login credintals e.g. email and password.
- server verifies the credentials against the database.
- server creates a temporary user session. 
- server stores the session in the database.
- server issues a cookie with a session ID.
- user sends the cookie with each request.
- server validates it against the session store and grants access.
- when user logs out, server destroyes the session and clears the cookie.



![Stateful flow](https://res.cloudinary.com/practicaldev/image/fetch/s--jzM6Wq6e--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://cdn-images-1.medium.com/max/800/0%2AP5OxJMihg0S0jyqk.png)


## Stateless authentication

Token-based authentication enables users to obtain a token that allows them to access a service and/or fetch a specific resource without using their username and password to authenticate every request. Because the token can be a self-contained entity that conveys all the required information for authenticating the request, it is often referred to as stateless authentication. In this case, the server side does not need to maintain the state of a user.

The authentication token is created by the authenticating service and contains information to identify a particular user and the token validity. The token itself is cryptographically signed to prevent tampering.

After the token is validated by the service, it is used to establish security context for the client, so the service can make authorization decisions or audit activity for successive user requests.

## flow for statless


- user submits login credentials, e.g. email and password.
- server verifies the credentials against the DB.
- server generates a temporary token and embed user data into it.
- server responds back with the token. 
- user stores the token in client storage.
- user sends the token along with each request.
- server verifies the token and grants access. 
- when user logs out, token is cleared from client storage.
- server verifies the credentials against the database. 


![statless flow](https://res.cloudinary.com/practicaldev/image/fetch/s--xAjXADfz--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://cdn-images-1.medium.com/max/800/0%2A16xpkdbQ1tuFphvs.png)


## Advantages and disadvantages:
||Stateless | Stateful |
|-|-|-|
| storage | reduces memory usage | increase memory usage |
| distributed servers | easy to support  | state synchronization logic   |
| Url linkability | possible | not possible |
| Secret Key | can be compromised | no secret Key |
| manage client from the server | hard | easy |
| complixity | hard to understand | easy to understand |
| Revoke the session | ask users | anytime |

## When to use?
There really isn’t a preferred method for authentication, both methods can be used interchangeably or together to create a hybrid system. It all boils down to the developer and the use case.
However, it is worth noting that token based authentication scales better than that of a session because tokens are stored on the client side while session makes use of the server memory so it might become an issue when there is a large number of users using the system at once.






