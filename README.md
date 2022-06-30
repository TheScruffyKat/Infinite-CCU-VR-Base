# Infinite-CCU-VR-Base
**Comes with GorillaLocomotion bult in and setup for networking**

Uses EOS and custom systems to achieve infinite CCU for free!

> I Highly reccomend you to read through the quick start guide bellow before you jump in!

## Important Notices Before Usage!
It is recommended not to change any EOS components as it may put you and others at risk of leaking IP's

Make sure this option on the EOS Transport (NetworkManager GameObject) is set to Force Relays else IP's may be leaked (including yours)

Not importing mirror properly? Please do NOT use the latest version from the asset store as it wont work. Instead get it from here as a .unitypackage and import it into your project.

> ⚠️ Just in case, I am not responsible for IP leaks, TOS breaking or other stuff similair, as you need to read the EOS TOS first!
> 
> [Epic Online Agreements](https://dev.epicgames.com/en-US/services/terms/agreements)

# Things to know to create your game! (QuickStart Guide)

**Most of this requires a Network Identity on any object that will interect with ANY of the networking!**

> When scripting, you will probably need to add ```using Mirror;``` to the top of your script

## Running functions over the network
This can be used to do things such as award a point, change your colour, or anything that you can think of with functions but over the network!

**Sending a function to the server**

```
[command]
void myTestFunction(string name) {
  Debug.log("I as the server recieved a call from " + name);
}
```

**Sending a function back to the clients**

```
[ClientRPC]
void nameFromServer(string nameBack) {
  Debug.log("Server sent me the name " + nameBack);
 }
```

## Using both functions together
This script sends a name to all clients and makes them log them in the console when sendName is called with a name (string) input.
```
[command]
void sendName(string name) {
  Debug.log("Sending name...")
  sendBackToClients(name);
}

[ClientRPC]
void sendBackToClients(string name) {
  Debug.log("I recieved the name " + name);
}
```

[Learn more about this topic here!](https://mirror-networking.gitbook.io/docs/guides/communications/remote-actions)

## Syncronising gameObjects


To syncronise a game object, you can add a NetworkView component as well as one of these that you want to be synced (These are the mains):
- Network Transform (Position, Rotation, Scale)
- Network Animator (Animations)
- Network Rigidbody (Physics based movements that need to remain smooth and interactible with no errors, such as a rolling ball)
