# Reading Notes 14 -- BCrypt

## Password Hashing

From [Auth0](https://auth0.com/blog/hashing-passwords-one-way-road-to-security/)

Storing passwords on the server takes some care. If we store sensitive data in cleartext it makes it easy for an intruder to gain all the passwords in the database plus many users reuse passwords making other services at risk too.

Hashing is a way of transforming data to make it unreadable. The mathematical algorithms for hashing are one way but the same data will always produce the same hashed result. Passwords can be stored as hashes and even if they were stolen the attacker would not be able to reverse -- or at least be too annoying to try, that's the hope. 

Rainbow tables for common hash algorithms are available for attackers to use and common passwords can be looked up via the table. To combat these tables extra random "salt" can be added to the data to produce a different hash.

Cryptographic collisions occur when two pieces of data produce the same hash. Hashes will have a set size and the input data can be any size, this is why collisions occur. This can be exploited and is called a collision attack.

As computers increase in power breaking hashes happens, hashes that were once thought to be strong are now considered unsafe.


## BCrypt Overview

From [Dan Boterhoven's Medium](https://danboterhoven.medium.com/why-you-should-use-bcrypt-to-hash-passwords-af330100b861)

Bcrypt's aim is to allow users to secure information with a cryptomatic algorithm based on the "Blowfish block cipher". BCrypt uses an adaptive hashing function that makes use of a Key Factor.


## JBCrypt

From [Mindrot.org](https://www.mindrot.org/projects/jBCrypt/)

JBCrypt is a Java library that uses OpenBSD's password hashing code. Example:

```java
// Hash a password for the first time
String hashed = BCrypt.hashpw(password, BCrypt.gensalt());

// gensalt's log_rounds parameter determines the complexity
// the work factor is 2**log_rounds, and the default is 10
String hashed = BCrypt.hashpw(password, BCrypt.gensalt(12));

// Check that an unencrypted password matches one that has
// previously been hashed
if (BCrypt.checkpw(candidate, hashed))
	System.out.println("It matches");
else
	System.out.println("It does not match");
```
