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

Password Storage
---

Rule number one: Do not store password in plain text. There are mainly two ways of storing passwords:
  * Encryption:
     Two way function that is reversible, meaninig it can be decrypted to      get the orginal string if you have the key. The first step is the 
      `plain text + private key = encrypted password`
      `encrypted + key = original password`  
  * Hashes:
     One step function that is irreversible `parameters + input = hash`. If passwords are going to be stored they must be hashed.
  * Key Derivation Functions:
     `[hash] + [time] = [Key Derivation Function]`   
       
Password Strength
---

The length of the password alone does not suffice, passwords must also be sufficiently complex. GRC website to verify the strength of your password.

# Bcrypt
---

Bcrypt is a library on NPM that makes it easy to `hash` and `compare` passwords in Node enviroment.

Add Bcrypt

```
yarn add bcrypt
```

Import

```
const bcrypt = require('bcryptjs');
```

Hash Password 

```
const credentials = req.body;
const hash = bcrypt.hashSync(credentials.password, 14);
credentials.password = hash; 
```
    

Password Verification 

```
const credentials = req.body;
<!--  find the user in the database by it's username then -->
if (!user || !bcrypt.compareSync(credentials.password, user.password)) {
return res.status(401).json({ error: 'Incorrect credentials' });
}
```
   
