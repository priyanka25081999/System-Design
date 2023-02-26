You are able to resume a movie from wherever you left the last time in Netflix and other OTT platforms. Let’s see how much engineering goes behind building this feature.

1. You would have to inform the Netflix server that you watched it till this point. This request you have to make is while you are streaming. Now, this request can be at times dependent on how much granularity of data you have to store. If you want to store data accurately for 1 second, then you have to make a request every second.

2. A simple design would be to send a request and store the data in the database and then return a response. This design would work flawlessly for some number of customers. But, it will cause issues when you start serving a million users. Why? Because since this request is being sent while you are streaming, the latency of this request has to be extremely low. Storing the data in the database and then returning a response can take a lot of time which might be caused by storing the data in db.

3. What’s the solution to this? Asynchronous processing. You don’t care about the watch history while you are streaming. You only care about it only when you have to start watching it again from a certain point. This means that the processing can be deferred.

4. To solve this, they introduced a Kafka messaging queue where they just put the message and return in response an acknowledgment that the message has been received and the processing of the message is deferred for a later time.

5.  But this doesn’t solve the problem completely. There can be many issues with this approach too. What if while publishing a message to the queue the request fails? What if the processing of a message in the queue fails?

6. One major issue is ordering. Your requests that you send must be processed in that order itself or there should be a way such that even if they are processed in a different order, the end result is the same. You can do this in 2 ways: sending timestamps in requests or keeping distributed counters.
