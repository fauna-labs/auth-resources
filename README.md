## Authentication with Fauna 

This repository bundles authentication resources together. These  contains unofficial patterns, sample code, or tools to help developers build more effectively with [Fauna][fauna]. All [Fauna Labs][fauna-labs] repositories are provided “as-is” and without support. By using this repository or its contents, you agree that this repository may never be officially supported and moved to the [Fauna organization][fauna-organization].

---



### Guidance

- **Blog:** [Choosing an authentication strategy with Fauna](https://fauna.com/blog/choosing-an-authentication-strategy-with-fauna)

More blogs inline along with the resources listed below. 



### Blueprints

[Blueprints](https://github.com/fauna-labs/fauna-blueprints) are pure FQL solutions that can be set up easily with the [Fauna Schema Migrate](https://github.com/fauna-labs/fauna-schema-migrate) tool. Since they are pure FQL and no specific backend or framework frontend code, they are typically not the complete solution (e.g. you can not yet send emails from pure FQL, nor set httpOnly cookies). They do provide an easy to set up Fauna API to create such functionality. 

- **Blueprint:** [Email verification](https://github.com/fauna-labs/fauna-blueprints/tree/main/official/auth/email-verification), verify a users email based on verification tokens. Two functions are provided, one to request a token, one to verify the user.
- **Blueprint:** [Password reset](https://github.com/fauna-labs/fauna-blueprints/tree/main/official/auth/password-reset), a blueprint that implements a password reset flow in FQL. The blueprint provides the means to request a token (that can then be send to the user via email or other means) and a password reset function that operates with this requested token. It also provides a password change function which verified the previous password for logged-in scenarios. 
- **Blueprint:** [Basic register/login/logout](https://github.com/fauna-labs/fauna-blueprints/tree/main/official/auth/register-login-logout), a simple register, login and logout implementation in pure FQL. 
- **Blueprint:** [Basic refresh tokens](https://github.com/fauna-labs/fauna-blueprints/tree/main/official/auth/refresh-tokens-simple) a refresh flow in pure FQL.
  - **Blog:** a blog was written that [explains the blueprint implementation](https://fauna.com/blog/refreshing-authentication-tokens-in-fql).
- **Blueprint:** [Advanced refresh tokens](https://github.com/fauna-labs/fauna-blueprints/tree/main/official/auth/refresh-tokens-advanced), an advanced implementation of a refresh flow with leaked token detection and other advanced features. 
  - **Blog:**  ablog was written that [explains the blueprint implementation](https://fauna.com/blog/detecting-leaked-authentication-tokens-in-fql). 



### Skeleton applications

- **Skeleton app:** [Fauna authentication from the frontend](https://github.com/fauna-labs/fauna-auth-skeleton-frontend) 

  Authentication from the frontend by using User Defined Functions (UDF) to create user tokens and bootstrapping the process with a key that can only call these two UDFs.

- **Skeleton app:** [Secure Fauna authentication in client-serverless](https://github.com/fauna-labs/fauna-auth-skeleton-backend) 

  Authentication from the frontend by using User Defined Functions (UDF) to create user tokens and bootstrapping the process with a key that can only call these two UDFs. 

- **Skeleton app:** [Auth0 authentication + Fauna from the frontend](https://github.com/fauna-labs/faunadb-auth-skeleton-frontend-with-auth0) 

  Authentication from the frontend that relies on the Auth0 react library (@auth0/auth0-react) to authenticate and takes advantage of Fauna's Identity Provider functionality to accept Auth0 JWT tokens. Auth0 makes authentication easy, it's a  service that provies authentication and auhtorization functionality which can now seamlessly be combined with Fauna. Auth0 is he system is perfect if you need to add social authentication to your applications but can do much more. This implementation has been covered in two separate blog posts. 

  - **Blog:** authentication and setup: https://fauna.com/blog/setting-up-sso-authentication-in-fauna-with-auth0
  - **Blog:** authorization: https://fauna.com/blog/setting-advanced-role-based-access-patterns-in-your-spa-with-fauna-and-auth0

