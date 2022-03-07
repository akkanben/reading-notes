# Reading Notes 16 -- Spring Authentication

From [Spring.io Guides](https://spring.io/guides/topicals/spring-security-architecture)

## Authentication

**Authentication** is security that is concerned about making sure a user is who they say they are.

In Spring the main strategy interface is `AuthenticationManager` which can do three things in it's `authenticate()` method:
- Return an *Authentication* object.
- Throw an *AuthenticationException*
- Return null when Spring is not sure which to do.

The *ProviderManager* can handle a chain of *AuthenticationProviders* when various mechanisms are required. *AuthenticationManagerBuilders* can be used to aid managing custom setups.

## Authorization

**Authorization** is security that enforces access control and is about what a user is allowed to access.

Spring uses the *AccessDecisionManager* as the main way of handling authorization. It manages a chain of *AccessDecisionVoter* instances. These instances consider an *Authentication* and a secure object that has various attributes. The object can represent a variety of data like a web resource or a Java method from a class.

The default for *AccessDecisionManager* is to allow access if any of the voter instances return affirmatively. An example from the guide for *ConfigAttributes* that use "SpEL" is `isFullyAuthenticated() && hasRole('user').

## Web Security

Spring uses *Servlet Filters* to control requests. The filters form a chain and a single filter can veto, or even modify the request. The filtering order is controlled through a *@Bean* filter that can have an *@Order*. The Spring security mechanism should be seen as a single filter but one that can have a chain of filters contained in a *FilterChainProxy*.

## Method Security

Spring also offers built in support for Java methods. Access rules can be created in the same format as the *ConfigAttribute* strings. Method security can be combined with web security allowing for more granular security structure. Although not common for user applications it is possible for custom security to use an async technique to allow for background processing -- because Spring's *SecurityContext* is thread-bound.

