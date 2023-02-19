Ever wondered how a chat application works?

1. The one thing that makes a chat application differ from a lot of generic applications is that you don’t request anything from the server. 
   Still you are able to receive what the other person sent. How will the server push the message to the receiver without receiving any request from 
   the receiver? Let’s consider 2 scenarios. In one you are online, in the other you are offline.

2. What happens when you are online ? For any HTTP response, you get from a server, you have to send a request first. But, this model would not work 
   for a chat application.

3. If we have to incorporate such a model, every receiver(client) would have to keep polling the server for a message by sending continuous HTTP requests. 
   But, that would cause the server to be overloaded and will also defeat the purpose - which is real time chat.

5. For all the above purposes, we cannot use HTTP protocol for a chat application. For a chat application, XMPP protocol is used which allows bidirectional 
   chat, i.e will allow the server also to push the messages to the client. Websockets can also be used for this.

6. To maintain the connection with the server while online, would require a connection to be open at all times with the server. 
   At layer 4, TCP is used to create a persistent connection.

7. But what if you are not online? There is no persistent connection with the server. This means the server cannot push a message to your phone directly. 
   Then how do you get push notifications?

8. This is where cloud messaging servers come into play. There is one connection always maintained with these servers depending on your phone OS.

6. Whatever application has to send a notification, can send the notification to these servers which can then forward the notification through 
   the open connection with the server.
