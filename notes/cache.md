**Cache**

* Use-cases:
  
  1. To save network calls: When you're querying the commonly used data. Example: You have stored user profiles in the database and the user is asking to get the profile multiple times.
     So, in this case you can store the profile (key-value pair format) in the cache which is your in-memory cache.
     
  2. To avoid competitions: Example: you want to know average age of all users in your system. So everytime when user asks for the average age, you go to the database, get all the users,
     find the average of all users age and return that result. This is expensive operation. The better way is find the average age in above way once and store the result in the cache (key-value
     pair format).

  3. Avoid load on the database: When we have multiple servers and all are hitting and sending requests to database, then there is a huge load on the database. So instead you can keep the
     information in cache. So, you can hit the cache and avoid hitting the database.

* You can't store every information in the cache, bcz the hardware on which the cache runs is more expenesive than that of the a normal database. Also another reason is if you store tons of data
  in a cache, then the search time will increase. It doesn't make sense to use cache.

* Cache Policies: The way you decide for loading and evicting data from cache is called a cache policy.

  1. LRU (Least Recently Used) - mostly commonly used policy (popular). While putting data, put it on the top and when you need to remove some item then remove the one who is on the bottom.
     That means the least recently used entries of the cache.
     
  2. LFU (Least Frequently Used) - these are sliding window based policies.
 

* Thrashing: A situation where the cache is constantly being filled and emptied with data, resulting in a high cache miss rate and poor cache utilization. Mostly, this happens when the cache is too small relative to the data being accessed by the processor.
 
* Consistency problems: For example, you have multiple server and one of the server updates the profile value in the database and the client wants to get the value. Then your server gets it from the cache which has the outdated value and serves it back. It causes data consistency issue. So the cache can be placed near to the database or near to the servers. So you can also have **global cache**. So, all the servers can update the data and if any of the server crashes then no need to worry as the cache contains updated value always. Sometimes slower but accurate.
        
* Where do we place cache: Mainly use global cache. But for simplicity and faster response times, you can keep data in the local memory.
 
* Write Through/Write back cache:
    * Write Through: When you need to begin an update the data that you have in the cache. If you make an update directly to the database then there is going to be inconsistent data.
      So, make an update in the cache first and push that update to the database. That is the write through cache. Possible drawback is if you have multiple servers and few using global and few       using in-memory cache and having the same entry and if you update the entry in global cache then in-memory cache contains the older entry. So it again becomes inconsistent.
      
    * Write back: Hit the database directly. Once you have hit the database, make sure to make an respective entry in the cache. The drawback here is its quite expensive operation.
 
    * Hybrid approach: Solution to both of above drawbacks. So whenever there is an entry that has to be updated on the database. Don't write back immediately on database. If it's not the critical entry. And then after 10 or 20 seconds passes, take one single network call and then persist data into the database. So you are saving on hitting the database consistently. So, this can be hybrid policy.

So, we can choose any of the above policies based on our use case.
