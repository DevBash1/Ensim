# Ensim
Ensim official npm package for communicating with sim.

# Install

```
npm i -g ensim
```

# Usage

Create an instance and pass token as argument
```javascript
const ensim = require("ensim");

const auth = "auth_xxxxxxxx";

let sim = new ensim(auth);

```

Add listeners to listen for events from our server and your sim

```javascript
const ensim = require("ensim");

const auth = "auth_xxxxxxxx";

let sim = new ensim(auth);

sim.on("connect", () => {
    console.log("connected to server as: " + sim.id); // connected to server as: xxxxxxxx
});

sim.login(function(obj){
    if(obj.error){
        console.log(obj.message); // Invalid Auth Token
    }else{
        console.log(obj.message); // Authorized
    }
})

sim.on("message", function(obj){
    console.log(obj); //{ auth: 'auth_xxxxxxxx', message: 'Hello Yello!', sender: 'MTN', pend: true }
})

sim.on("offline", function(msg){
    console.log("Sim is offline!"); // Sim is offline!
})

sim.on("online", function(msg){
    console.log("Sim is online!"); // Sim is online!
})
```

Run USSD codes

```javascript
sim.ussd("*556#", function(obj){
    // Handle Response
})
```

To test your sim run command on terminal after installation.
```
ensim auth_xxxxxxxx
```
