Jordan has no life - Playlist - https://www.youtube.com/watch?v=bwt09KXDH94&list=PLjTveVh7FakLdTmm42TMxbN8PvVn5g4KJ&index=2

1. Database Indexes:
    * Requirements: a. we want to store data persistently b. We want it on hard-drive as RAM is volatile so it's more durable on hard drive c. Hard drive is on database.
    * Hard Drive: The closer you put the data on hard drive, the faster you access the data. So, there is a better read speed
    * When we write data to table: To read a record we can search a record one by one it requires O(N) time, and for write too we first need to search the record and edit it so take O(N) times.
    For write, instead of searching the record, we can simply go to the bottom of the table and write the new row of same record by editing the required fields. So, write will now take O(1) time.
    But the read is still heavy - O(N). It's not good enough solution for both read and write
    * Database Indexes:
       a. Read operation: Indexes are specifically designed to speed up read operations by providing a quick lookup mechanism. Instead of scanning the entire table,
          the database engine can use the index to quickly locate the relevant rows. This is particularly useful for SELECT queries with WHERE clauses or JOIN operations i.e range queries.
       b. Write operation: When data is written to a database, it may need to be inserted into multiple indexes. This means that every write operation not only involves adding data to the main table
          but also updating the associated indexes. This additional overhead of maintaining indexes during write operations can slow down the process.

2. Hash Indexes:

    * We are here bcz of 2 reasons: 1. O(N) read 2. Go through each and every record/row
    * Hash function -> HashFunction(Key) --->(returns)--> value, so we then store this key and value in an array for example. So it allows O(1) read and write
    * It might possible that 2 keys can get same value when using hash function, so in that case, we can apply chaining.
    * Issues with hash maps:
         1. Hash maps are bad on disk - Using hash function we can get any values (evenly distributed) so on disk it's also stored in distributed way. Hence the performance is very poor.
            That means, hash indexes are always kept in memory. but it also has few other issues. One is that the memory is expensive. Also RAM is not durable, its volatile. 
            To overcome it, we use WAL (Write Ahead Log) - Using it we can repopulate the hash index even if the data in RAM is lost.
         2. We can't do range queries - If we want to get specific key then using hash map we can do it in o(1) but if we want to get from key1 to keyN then we literally have to loop through
            all the keys between key1 and keyN, its not feasible, bcz there can be multiple names between key1 and keyN. So, its again O(N) and we need a better solution to fix it.
            We can might think of binary search tree for range queries which can work more better for range queries but then for read and write it takes O(logN) which is worse than hash indexes.
      * Conclusion - Hash indexes are good for read and write, both O(1) time. But not good for range queries. But, its good for small data sets.

3. B-Tree Indexes:
    
