HTTP Protocol
-------------

1. HTTP is a **HyperText Transfer Protocol**, it is considered the basis for **data communication between networked devices**.
2. Suppose there are set of clients which are connected to a server, each of them maintaining the HTTP connection to have a request. The main use HTTP in every website is loading the initial HTML/JS website(images, videos, name, logo, etc.), i.e to **fetch the assests and load the website** in your browser. Later you can start interacting with the server. 
3. HTTP is a layer 7 (Application layer) protocol, where the HTTP connection will be made between browser and the application. At layer 4(Transport layer) HTTP uses TCP protocol. The TCP connection will be made between client and the server.

#### How does HTTP and TCP work with each other ?
1. When you make any call to the server, then the browser has to establish a **TCP connection** with the server. This connection establishment requires several round-trips of information between client and the server, this is called **Handshaking**. HTTP **depends on** this connection to fetch the data. 
2. TCP handshaking is the **3 way process**, where client first sends the request to the server then the server sends back the response to the client as "okay, you can create the connection" and then client sends back the acknowledgement to the server. As there are many data packets being transfer to establish the TCP connection, this process takes some time.
3. This time is depends on the location of the server that you are trying to access, the server can be local, intercontinental, transcontinental. 

#### HTTP versions and facts:
1. **HTTP 1.0** : The first major generation used was the HTTP 1.0. With this version, there were some restrictions that only one request can be made per connection. That means for each request which we made from brower, a new connection will be established. So, this was very expensive process.
2. **HTTP 1.1** :
     * **Persistent connection** : HTTP 1.1 came up with an approach called **persistent connection** to overcome the above problem. A persistent connection is one that remains open for limited  amount of time. 
     * Now, why it has to stay open ? because, if you close the connection, then you would again have to re-establish/re-initiate the TCP connection. 
     * Then, this open connection can be reused for several requests, which saves the time for new TCP handshake for each connection request. 
     * **Problem** with this arrangement is that one request has to wait for the other request to complete. While loading a webpage, multiple request has to sent from client to server to fetch the assets. So, sequential requests slows down this process of fetching the assets (that is, first make a call to load the image, then video, then logo of the website, so this is sequential). To overcome this, HTTP 1.1 came with the idea of **pipelining**. 
     * **Pipelining** : HTTP pipelining is a technique where several HTTP requests are sent on the single connection channel without waiting for the corressponding responses. That means, second request does not wait for the response of first request. Client can send parallel requests to the server. This HTTP pipeline did **speed up with the process of loading the HTML pages**, but multiple problems incurred with it. Problems are server must send the response in **FIFO order** and another problem is **HOL blocking**. HOL blocking occures when heavy assests load request is sent first to the server, then other requests will be blocked on it. 
3. **HTTP 2.0** : To resolve the above issues, there came HTTP 2.0 which came with **multiplexing**. Multiplexing is that, the server can return responses in any order and then web browser processes it to make the page. This also suffers an issue as there is **parallelization** on one single TCP connection. If that connection is lost (probably your internet got disconnected), then even the successful requests are lost. 
4. **HTTP 3.0** : To overcome the above, there came HTTP 3.0 which **runs on QUIC instead of TCP** to solve this issue.




