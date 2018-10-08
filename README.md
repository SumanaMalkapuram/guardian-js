About
=====

Shows how to display guardian authenticator options based on the user authenticated connection.

Setup?
=================

1. Setup multiple enterprise connections. 
2. Provide the list of connections and their authentication methods to guardian-hosted.html. sample below

```
var connectionToMFAMapping = {
        "adfs-asurion" : ["push"],
        "adfs-gep" : ["sms", "otp"],
        "adfs-exxon" : ["sms"],
        "other" : ["sms", "otp", "push"]
         };
```
3. Deploy the html to Guardian Hosted login page in Auth0 Dashboard.
4. Enable Guardian MFA for Push and SMS.



