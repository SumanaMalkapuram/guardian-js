About
=====

Shows how to display guardian authenticator options based on the user authenticated connection.

Setup
=================

1. Setup multiple enterprise connections on Auth0 Dashboard. 
2. Create a backend API with all the connection and desired methods (authentication types) against each connection. 

```
app.get("/connection/:userinfo", function(req, res) {
        var defaultConnection = "other";
        // Build the list of connection names and their mapped guardian authentication types.
        var connectionToMFAMapping = {
        "adfs-asurion" : ["push"],
        "adfs-gep" : ["sms", "otp"],
        "adfs-exxon" : ["sms"],
        "waad" : ["sms"],
        "other" : ["sms", "otp", "push"]
        }
        var user = req.params.userinfo;
        var user_array = user.split("|");
        console.log(user_array);
        var userAuthenticatedConnection = user_array[0];
        var userConnection = _.has(connectionToMFAMapping, userAuthenticatedConnection) ? userAuthenticatedConnection : defaultConnection;
        res.status(200).send(connectionToMFAMapping[userConnection]);
           
    });
```
3. The API would return back an array of methods defined for a connection.
4. Deploy the html file against Guardian hosted login page.



