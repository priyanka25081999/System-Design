Instagram launched its live video feature and its app went down as soon as Drake started a live video. Want to know what happened?

They suffered from something called **thundering herd**.

 What was this problem and what are some ways to resolve this?

 1. Thundering herd as the name suggests occurs when a lot of requests compete for the same resource. Let's understand this with the help of an example.

 2. Suppose a celebrity starts a live video and a lot of people want to join it. Since, the celebrity is big, the number of fans watching the video are also big.

 3. Now, due to some reason, the video chunk that had to be served, is not yet updated in the cache. How will the users see the video now ?

 4. The requests will now all be sent to fetch the video chunk from the persistent data store. All the requests want the same video chunk. 
    There are millions of requests asking from the same chunk from the data store. The data store CPU utilization goes high because of concurrent connection 
    and the server crashes. Stampede caused the server to die.

 5. How do we save the server now ? We somehow want to prevent millions of requests asking for the same piece of data at the same time. Most intuitive thing to 
    do is use one request to bring the chunk in cache and answer the other requests through the cache after that. But how do you do this ?

 6. One solution which comes to mind is to take a lock. But locking means more time to fetch the chunk. We can't compromise on the speed. We need to think more.

 7. What if we could somehow mark, that the data being requested from the data store is already being fetched through some other earlier request ?

 8. This is what instagram did. They used something called a promise. A Promise is an object that represents a unit of work producing a result that will be 
    fulfilled at some point in the future. You can “wait” on this promise to be complete, and when it is you can fetch the resulting value.

 7. So, as soon as you get a request. Set a value in a database which acts as a signal that this data is already being fetched. The other requests simply wait for 
    the promise to get fullfilled and then execute and are able to find the chunk in the cache itself.

Resource - https://lnkd.in/gptgMM22
