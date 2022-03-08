# Reading Notes 17 -- Spring Authorization

Spring Boot can handle its authorization with OAuth. Using OAuth we can take advantages of external services to handle the login: Google or GitHub.

- To get started add the Spring Security OAuth dependancy to the project. 
- Add a OAuth application to your GitHub account.
- The Authorization callback URI template is `{baseUrl}/login/oauth2/code/{registrationId}`.
- A "application.yml" file is used to link to GitHub.

Using OAuth like this will allow the app to stay signed across refreshes or even if you open a new browswer -- as long as the browswer is logged into GitHub it will stay logged into the app.

- We can use the Authentication Pricipal on routes to grab attributes.
- Use the @RestController annoation on the controller.
- Use the WebSecurityConfigurerAdapter to handle the filters.
- A post to "/logout" will logout the session.

The "application.yml" file can be edited to detail a Google account client-id/client-secret similar to the GitHub details.
 
- Easily add links for sign-ins: `<a href="/oauth2/authorization/google">click here</a>`
- OAuth can be used for authorization on local databases too.
- An "AuthenticationFailureHandler" can be setup to handle error messages and then the error message attributes can be added via the HttpServletRequest in a GetMapping route.
