1. In 2011, Pinterest gained traction and became the highest-growing startup of those times. 
   They had both SQL and NoSQL databases at play which were crashing a lot because of increasing load. They decided to shard their MySQL database.

2. They had their database in the form of master-slave architecture. To keep things simple, they decided to do no writes to slaves. 
   Slaves will just serve as a read replica which they suggested as an approach for others also because managing writes from multiple slaves can lead to lots of consistency issues. 

3. For backups, they relied on master-master replication. Master-master replication offers various benefits over master-slave replication. 
   In master-slave replication, if the master goes down, one of the slave is used to create the new master. This creates a single point of failure. 
   In master-master replication, writes can be sent to both masters and if one of the masters goes down, then still, there is another master alive and 
   the slaves of the failed master can be attached to the other master. Both masters can have their own set of slaves as read replicas. At any point, a new slave can be added if required.

4. Pinterest initially started with 8 MySQL instances which will store different shards of data. Each instance could have multiple shards and the information on 
   what shard is present in each replica is stored in a configuration file which is replicated and managed with the help of a zookeeper.

5. Pinterest has multiple tables for pins, user_liked_pins, boards etc. For each of the table they use the same sharding strategy but the data for different tables 
   connected to each other can be in different shards. So, they keep two types of tables - object tables which store pins/boards, etc and then the mapping tables which 
   store the mapping between those.

6. They created a 64 bit id which contains the shard id - 16 bits, type ID- 10 bits and local ID which is 36 bits. The remaining 2 bits are left for any future expansions.

7. Now during an insert, shard ID is determined for a pin/board and the type is already decided. For example, pin is type 1. Now the json is inserted into the selected shard and 
   the db returns a local ID. Now these 3 can be combined to get the 64-bit Id which can be used in mapping tables.
