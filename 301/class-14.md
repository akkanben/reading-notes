# Reading 14 - Authentication

From CSO article [What is OAuth](https://www.csoonline.com/article/3216404/what-is-oauth-how-the-open-authorization-framework-works.html)


1. What is OAuth?
  - OAuth is an open authorization standard that lets users grant websites access to their information on other websites and this all happens without sharing passwords.
2. Give an example of what using OAuth would look like.
  - You want an app to be able to work with media on a social network profile, you could authorize this app to access your social media information and the app would end up with an access token.
3. How does OAuth work? What are the steps that it takes to authenticate the user? (I tried summarizing this but had to end up just taking it directly from the csooline site liked above).
  - The first website connects to the second website on behalf of the user, using OAuth, providing the user’s verified identity.
  - The second site generates a one-time token and a one-time secret unique to the transaction and parties involved.
  - The first site gives this token and secret to the initiating user’s client software.
  - The client’s software presents the request token and secret to their authorization provider (which may or may not be the second site).
  - If not already authenticated to the authorization provider, the client may be asked to authenticate. After authentication, the client is asked to approve the authorization transaction to the second website.
  - The user approves (or their software silently approves) a particular transaction type at the first website.
  - The user is given an approved access token (notice it’s no longer a request token).
  - The user gives the approved access token to the first website.
  - The first website gives the access token to the second website as proof of authentication on behalf of the user.
  - The second website lets the first website access their site on behalf of the user.
  - The user sees a successfully completed transaction occurring.
4. What is OpenID?
  - OpenID in its reinvented form as OpenID Connect is the authentication layer for OAuth. Previously it competed with Facebook Connect to handle multiple logins for multiple websites.


From the [Auth0 Docs](https://auth0.com/docs/authorization/flows)


1. What is the difference between authorization and authentication?
  - Authentication is about making sure the user is who they say they are. Authorization determines what a user is allowed to access.
2. What is Authorization Code Flow?
  - It is what exchanges an authorization code for an access token server side.
3. What is Authorization Code Flow with Proof Key for Code Exchange (PKCE)?
  - Mobile and os native apps require additional security so PKCE handles that.
4. What is Implicit Flow with Form Post?
  - A method of authorization code flow that is designed to be used for public clients where the client is unable to securely store the client secrents.
5. What is Client Credentials Flow?
  - It is an authorization flow when the user is not interacting, situations like cli scripts, daemons or services running and authorizing without direct user input.
6. What is Device Authorization Flow?
  - A authorization flow that allows a device to handle the input on behalf of another device.
7. What is Resource Owner Password Flow?
  - Not recommended, but for trusted apps can use a form for collecting username and password.

## What I want to know more about

- Reading about all these access tokens and secrets makes me want to know a bit more about how these work. Are they similar to how public key cryptography works?

