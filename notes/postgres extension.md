For example, you might use pg_cron to run a pg_partman function every month to create a new partition table for the 
upcoming month's data, ensuring the system always has partitions ready for new incoming data. 

* pg_cron 
Purpose: To schedule and execute SQL commands or functions at regular intervals within the PostgreSQL database. 
Functionality: It acts as an internal scheduler, allowing you to define jobs using cron syntax and execute them automatically. 
Use Cases: Automating repetitive administrative tasks like data backups, generating reports, rebuilding indexes, or running maintenance scripts. 

* pg_partman 
Purpose: To automate the management of partitioned tables, especially in databases with large volumes of time-series or transactional data. 
Functionality: It automates the creation of new child (partition) tables and the management (e.g., detachment or dropping) of old ones. 
Use Cases: Improving query performance by breaking large tables into smaller, more manageable units, and facilitating data archiving or 
purging by easily dropping old partitions. 

* How They Work Together
pg_partman creates the infrastructure for partitioning. 
pg_cron schedules the pg_partman functions to perform maintenance, such as adding new partitions or detaching old ones. 
For example, you might use pg_cron to run a pg_partman function every month to create a new partition table for the upcoming month's data, 
ensuring the system always has partitions ready for new incoming data. 
