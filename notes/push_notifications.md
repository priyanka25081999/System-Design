**Push Notifications**

How do push notifications work?

1. Why do we need to even discuss this topic in system design? Push notifications seem fairly simple. Just a simple API call, right?

2. But, push notifications do not go from client to server. In this, the server has to push something to the user when the client is not asking anything.

3. When we get notifications, our phone has not opened those apps, that means there is no connection of the phone with the backend servers.
4. If that was the case, there would always be some background processes running for each app always maintaining the connection with backend servers. But, that is not the case.

5. Our internet mostly works with pull based protocols(HTTP). The client makes a call and then gets a response. But, in case of push notifications,
6. we need to get a response without even making a call.

7. This is where cloud messaging servers come into play. There is one connection always maintained with these servers depending on your phone OS.

8. Whatever application has to send notification, can send the notification to these servers which can then forward the notification through the open connection with the server.
