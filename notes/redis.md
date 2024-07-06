**Redis**
Redis - 
1. stands for remote dictionary server is an in-memory database. It is an open source, in memory data structure store that can be used as database, cache, msg broker and streaming engine.
2. It supports multiple data structures such as hash, list, set, sorted set, bitmap, streams, bitmap etc
3. Due to this redis can be used to create variety of applications such as realtime chat, media streaming, msg buffers, auth session store, gaming leaderboards, realtime analysis etc.
4. Redis gives good performance and its also simple to use

5. Every opertion that we fire on the redis is **automic** in nature. Automic here means, when command is executing redis does not context switch and start executing other command. 
Example: if you have fired 3 commands then redis execute 2nd or next command only when it finishes the first command (it does not context switch).
6. Data is stored **in-memory** hence the most common use of redis is for **caching**. But redis also provides configuration persistence (you can manually also provide the configuration) or you can also configure it as no presistence at all, so whenever anything is crashed it is okay to loose the data.
7. Other key features are: transactions, pub/sub, ttl on keys and lru eviction

8. Assume you have a single process say postgres process and you want it to handle multiple processes simultaneuously at a time in single process mode.
First approach of doing it is using multithreading model. so whenever a new client gets connected to the database you spin a new thread and then that thread handles the request coming in from that client. It leads to a problem of data correctness. if we have k=10 and 2 threads are incrementing the k++ so possible answers can be 11 or 12. so we have to use safeguards like mutex or semaphore.

2nd approach which redis adopts - I/O multiplexing: With this, you achieve apparent concurrency (not true concurrency)
  - With threads, it is possible that 2 threads are scheduled on 2 different cores, so you are getting true concurrency.
  - Lets say you have 2 servers connecting to each other and 1 server wants to read data from socket it then fires the read() system call and the read system call is blocking, that means the call would not proceed until my connected client sends something over the network. This is painful, you are not making in progress while waiting for the read call (i.e I/O operation), So the idea of multiplexing is can we do multiple task while waiting on the I/O. Hence we cannot send read() I/O system call unless we know that there is someone who can send the data.
  - So the core idea is use of i/o monitoring calls to monitor the sockets and fire **read** on the ones that have some data. this is how redis also works it.
  - So, in redis, network I/O is slow bcz it waiting to receive the commands and in-memory ops are fast upon receiving commands redis can very quickly execute them.  





-----
1. Many people use it as a cache to improve the performance
2. However redis is fully fledged primary database that can be used to store and persist multiple data formats for complex applications.

How redis workd
1. it has redis core: which is a key value store, it already supports multiple types of data that can be 
2. 
