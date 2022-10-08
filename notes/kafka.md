### Apache Kafka

1. Apache Kafka is a **Distributed, Replicated Messaging Queue**. It functions like a **commit log**.
2. It is completely **open source** and we can download it directly. But to use it, we need to create an Apache Kafka cluster. 
   Because running Apache Kafka on just one system won’t work in a distributed environment.
3. A **cluster** of Apache Kafka contains **multiple servers**. Each server is called a **broker and stores the data**. 
   But where is the data stored? Apache Kafka makes use of secondary storage for storing the data. 
   A lot of people have apprehensions about hard disks being slower than the main memory. 
   We can make this access faster by writing and reading from sequential memory locations rather than random locations. 
   This is how Kafka stores data. How is this access sequential ? 
4. Regarding storage in Kafka, we always hear two terms - **Partition and Topic**. 
   **Partitions** are the units of storage in Kafka for messages. 
   **Topic** can be thought of as being a container in which these partitions lie.
5. Whenever we create a topic in Kafka, it creates the **directories equal to the number of partitions** we have specified - 
   One directory for one partition of the topic. In Kafka, the topic is more of a logical grouping, 
   and the **Partition is the actual unit of storage in Kafka**. That is what is physically stored on the disk. 

6. Each partition is further subdivided into **segments**. Each segment is a **log file containing the incoming messages**. 
   Each message which is stored in the log file contains the actual message along with the offset(number of messages in the file + 1) at which it occurs.

7. The messages as they come are written **sequentially in one of the partitions for that topic**.
   Each partition can be consumed by **only one consumer at a time**.(this is a kafka requirement, a consumer can read from multiple partitions. 
   But, one partition can be read from just one consumer.). 

8. A common operation in Kafka is to **read the message at a particular offset**. How will we find this offset? By Scanning the log file ? 
   But, scanning will take a lot of time. This is where the **index file** comes to help which stores the physical address for each offset.

9. Kafka does not always access disk sequentially but it does some things that make it much more likely that disk access is often sequential. 
   All Kafka messages are stored in larger segment files and since Kafka messages are **not deleted when consumed** (like in other message brokers) 
   Kafka will not end up creating a fragmented filesystem over time by continuously creating and deleting many variable length files.

10. Instead it creates **segment files** and then appends them to that file until it reaches 1GB(configurable). 
    When all messages in the segment expire, it deletes the entire segment.

11. More information about **Segments**:

        a. Kafka must periodically flush the data in the disk. 
        b. Even though the partition is an immutable data structure, it must purge the data based on the retention period. 
        c. Since deleting a single large file is error prone, a partition is further subdivided into segments. 
        d. Instead of storing all the messages into a partition, it is split into chunks called segments. 
        e. Whenever a segment has reached its max value, a new segment is created, and it becomes the new active segment.
        f. Inside the partition’s directory in the Kafka data directory, the segments can be viewed as index and log files.
