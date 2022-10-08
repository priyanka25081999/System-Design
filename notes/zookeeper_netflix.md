### ZooKeeper - Netflix overview

Netflix relies heavily on open source. They have their own version of a lot of different open-source technologies. 
One of it is the curator which is Netflix’s zookeeper library.

1. **ZooKeeper** is a **distributed coordination service** to manage a large set of hosts. ZooKeeper solves this issue with its simple architecture and API.

2. Apache ZooKeeper is a service used by a cluster to **coordinate between themselves and maintain shared data with robust synchronization techniques**. 
   ZooKeeper is **itself a distributed application** providing services for writing a distributed application.

3. Clients in the distributed application cluster, access information from the server. For a particular time interval, every client sends a message to the 
   server to let the sever know that the client is alive. Similarly, the server sends an acknowledgement when a client connects. 
   If there is no response from the connected server, the client automatically redirects the message to another server.

4. The zookeeper data model is quite unique. A **single unit of data stored in zookeeper is called znode**. First, you have a root znode represented by “/” 
   and then, there are **“config” and “workers”** namespaces. The config namespace actually stores the **data for configuration management** and 
   the workers node is used for **“naming”**.

5. Now the question comes, how are these clients notified of any changes in the configurations and make it available to all the connected “actual servers” 
   at the same time. This is accomplished through a mechanism called **watches**. Watches send a **notification to the registered client for any of the znode**
   (on which client registers) changes.

6. Znode changes are modification of data associated with the **znode or changes in the znode’s children**. Watches are triggered only once. 
   If a client wants a notification again, it must be done through another read operation. When a connection session is expired, the client will be disconnected 
   from the server and the associated watches are also removed.

7. If a client wants to store data in the ZooKeeper ensemble, it sends the **znode path and the data to the server**. The connected server will forward 
   the request to the **leader** and then the leader will reissue the writing request to all the followers. If only a majority of the nodes respond successfully, 
   then **the write request will succeed and a successful return code will be sent to the client**. Otherwise, the write request will fail. 
   The strict majority of nodes is called as **Quorum**.
