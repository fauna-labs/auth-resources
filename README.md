Authentication with Fauna 

This repository has moved to different repositories per approach to help new users find their way (see below)
The repositories that are available or will become available are listed below, this repository is kept online for the people who started following it, bookmarked it or want to see an overview of all auth skeletons I wrote.  

### Available: 
#### Skeleton apps:


- [Fauna authentication from the frontend](https://github.com/fauna-brecht/faunadb-auth-skeleton-frontend) 

  Authentication from the frontend by using User Defined Functions (UDF) to create user tokens and bootstrapping the process with a key that can only call these two UDFs. A blog post is on the way that details the implementation. 

- [Auth0 authentication + Fauna from the frontend](https://github.com/fauna-brecht/faunadb-auth-skeleton-frontend-with-auth0) 

  Authentication from the frontend that relies on the Auth0 react library (@auth0/auth0-react) to authenticate and takes advantage of Fauna's Identity Provider functionality to accept Auth0 JWT tokens. Auth0 makes authentication easy, it's a  service that provies authentication and auhtorization functionality which can now seamlessly be combined with Fauna. Auth0 is he system is perfect if you need to add social authentication to your applications but can do much more. This implementation has been covered in two separate blog posts. 

  - Authentication and setup: https://fauna.com/blog/setting-up-sso-authentication-in-fauna-with-auth0
  - Authorization: https://fauna.com/blog/setting-advanced-role-based-access-patterns-in-your-spa-with-fauna-and-auth0

#### Blueprints:
Blueprints are pure FQL solutions that can be set up easily with the [Fauna Schema Migrate]https://github.com/fauna-labs/fauna-schema-migrate tool. Since they are pure FQL and no specific backend or framework frontend code, they are typically not the complete solution (e.g. you can not yet send emails from pure FQL, nor set httpOnly cookies). They do provide an easy to set up Fauna API to create such functionality. 

- [Email verification] https://github.com/fauna-labs/fauna-blueprints/tree/main/official/auth/email-verification
- [Password reset] https://github.com/fauna-labs/fauna-blueprints/tree/main/official/auth/password-reset
- [Basic register/login/logout] https://github.com/fauna-labs/fauna-blueprints/tree/main/official/auth/register-login-logout
- [Basic refrehs tokens] https://github.com/fauna-labs/fauna-blueprints/tree/main/official/auth/refresh-tokens-simple
- [Advanced refresh tokens] https://github.com/fauna-labs/fauna-blueprints/tree/main/official/auth/refresh-tokens-advanced

### In progress:

- (still private, soon available) [Fauna authentication with backend, refresh flow with httpOnly cookies](https://github.com/fauna-brecht/faunadb-auth-skeleton-backend) 

  In this article we dive into writing a more secure authentication flow where we will use httpOnly cookies to store refresh tokens securely (tokens created in Fauna with specific permissions) and use short-lived access tokens in the frontend. The refresh token is stored in a httpOnly cookie which requires us to have a small backend that takes care of this specific flow but ensures that the refresh token (the more powerful of the two) is never exposed to the frontend. For other calls we have the option to therefore bypass the backend (if desired) and access the database directly from the frontend yet benefit from greater security since the token that will be exposed to the frontend will only receive access for a very short time which significantly limits the risks.

#### Planned / Early stage:

- Fauna + Auth0 from the backend

  Similar to the Auth0 implementation that relies purely on the frontend library we could implement a flow that involves a backend. 

  

- Fauna + Okta 

  Fauna's features to accept an Identity Providers JWT tokens also work for Okta, the setup would be slightly different, an example is coming. 



- Fauna + SuperTokens 

  In case you are storing your users in FaunaDB and want a secure session solution, then this may be the route to go. Using SuperTokens, you can create a `httpOnly` cookie session that can be used to communicate between your frontend and backend with automatic token refreshing and prevention of session fixation, CSRF, brute force and session hijacking attacks. The session will also allow you to retrieve Fauna user tokens (for the logged in user) on your backend or frontend, so that you can query FaunaDB with ease. SuperTokens is, of course, very new but looks promising and provided open-source libraries.
