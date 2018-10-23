# Authentication(authN) & Authorization(authZ)

Authentication has increasingly become very important mainly due to the human dependecy on computers, online services and the systems that hold our sensetive data. Authentication is the process where our Web API verifies the identity of the client making request to our resources. Authorization(authZ) is the process that follows to determine the kind of access the client should be granted.

In order to add authN to Web API there are manly four steps to be taken:
  * Registration of user accounts
  * Login to verify identity of the user
  * Logout to invalidate the user's access
  * Password reset procedure 

There are also three factors to take into account:
  * Password storage
  * Password strength
  * Brute-force safeguards

### Password Storage

Rule number one: Do not store password in plain text. There are mainly two ways of storing passwords:
  * Encryption:
    * Two way process:
      *

### Bcrypt

Bcrypt is a library on NPM that makes it easy to `hash` and `compare` passwords in Node enviroment.