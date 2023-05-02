**CockroachDB** is fascinating! Here are 5 key things that you should know about it ⚡

**1. Symmetrical Nodes**

In distributed data stores we generally see a few nodes more authoritative and privileged than others. But in CockroachDB the nodes are symmetrical and equally capable of handling any incoming request.

Every node in CockroachDB maintains a full membership list of all nodes in the cluster. This helps with maintaining quorum and ensuring data consistency.

When a new node joins the cluster, it must communicate with every other node to establish its membership status and receive a copy of the cluster's metadata.

**2. Load Balancing**

Symmetric Nodes make it really easy to place a load balancer. The load balancer need not be stateful or sticky and can route the request literally any node in the cluster.

**3. Data distribution**

In CockroachDB, the data is partitioned as contiguous ranges and each range is replicated thrice and distributed across the cluster. This helps with high availability and fault tolerance.

**4. Postgres Wire Format**

CockroachDB uses PostgreSQL wire protocol format which means any existing Postgres tooling and client can be used to talk to the database, and not require us to reinvent the wheel.

The wire format describes how SQL requests and responses are transmitted between the Client and the CockroachDB cluster.

**5. Request flow**

Request from the client goes to the Load Balancer, which is then forwarded to any symmetric node in the cluster. This node now acts as the "gateway node" and forwards the request to the node that owns the intended range.

The node that "owns" the range is the leaseholder. The writes are synchronously sent to the other two replicas to ensure strong consistency and high availability.
