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
     
  2. 
    
