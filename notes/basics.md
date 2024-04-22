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

    * 
       
    
