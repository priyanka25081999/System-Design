## Stripe Failure in 2019

Stripe went down for 2 hours in 2019. A lot of small businesses which sell their products through dropshipping and have a Shopify website, depend mostly on Stripe. 
A lot of them were not able to get their payments and suffered a lot. Let’s see and understand, what happened.

To understand what happened, we first need to understand, how Stripe stores data, which database it uses, and what the nuances involved.

1. Stripe is a **payment platform**, so it needs a database which can handle writes of millions of transactions happening every second. 
   So, their operation is **extremely write heavy**. Initially, they relied a lot on MySQL. But, now they have **migrated to MongoDB**.

2. Stripe splits data by kind into **different database clusters and by quantity into different shards**. Each cluster has many shards, and 
   **ach shard has multiple redundant nodes**.

3. In order to avoid losing any operations even if Stripe loses its database’s primary node, they structure their application such that all writes are **idempotent**. 
   Idempotent means that an **identical request can be made once or several times in a row with the same effect while leaving the server in the same state**. 
   This ensures that the transaction with an id happens just once,and does not reoccur even if retried. 

4. They wrap their calls to the **MongoDB driver in a retry block**. If the call fails because their MongoDB cluster is currently reconfiguring, 
   they try the operation again. But, this does not cause the transaction to occur twice because it is idempotent.

5. Three months before the outage, Stripe upgraded their databases to a new minor version. As part of the upgrade, they performed thorough testing in 
   their quality assurance environment, and executed a phased production rollout. The new version operated properly in production for three months, 
   including many successful failovers. But, something bad was creeping in.

6. The new version also introduced a subtle fault in the database’s failover system that only manifested in the presence of multiple stalled nodes. 
   On the day of the events, one shard was in the specific state that triggered this fault, and the shard was unable to elect a new primary.

7. Without a primary, the shard was unable to accept writes. Applications that write to the shard began to time out. Because of the widespread use of this 
   shard across applications, including the API, the unavailability of this shard starved compute resources for the API and cascaded into severe API degradation.

8. Stripe identified forcing the election of a new primary as the fastest remediation available, but this required restarting the database cluster. 
   Once we restarted these nodes, 27 minutes after the event began, the Stripe API fully recovered.
