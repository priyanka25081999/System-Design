# DNS

#### Ever wondered, what happens in the back when you type www.xyz.com in the browser ?
  The very simple answer is that it just maps the domain name (www.xyz.com) to the IP address and you are redirected. But, it actually quite complex process.
 
#### Let's begin with DNS (Domain Name System):
   1. DNS is a key part of internet infrastructure. It's basic function is to **map numbers to names**, like a phone book.
   2. At the bottle most level, DNS is a hierarchical database. It is also implemented as distributed databases which stores the various types of data,
      including hostnames and domain names.
   3. **Domain namespace** : The names in a DNS database from a hierarchical tree structure called the domain namespace.

#### Now, the question comes, who owns the database and how does the DNS resolution occurs ?
   1. **Resource record** : When you buy a domain from websites like Godaddy, an entry is made which maps the DNS name to particular IP address. This entry/record is
      called as Resource record.
   2. **Nameservers** : The resource records are distributed in **zone files**. These files are then distributed and cached across servers called nameservers, so
      that this information is stored in the DNS distributed databases and is available for the internet. 
      
#### Process:
   1. Whenever you type www.xyz.com in the address bar of browser, the nameservers determines the IP address and return it back to the client. These nameservers are
      of 4 types. 
   2. **Recursive resolvers** : These are provided by your ISP's (like godaddy, etc). If they have cached mapping of DNS mapping to IP address, then give back. 
      This is quite faster. If not, they make a further call to **root nameserver**.
   3. **Root nameservers** : A root nameserver accepts a recursive resolvers query which includes a domain name and the root nameserver responds by directing the recursive resolver to a TLD nameserver, based on the extension of that domain (.com, .org, .gov, .net, etc). 
   4. **TLD nameserver** : When a recursive resolver receives a response from a TLD nameserver, that response will direct the resolver to an authoritative nameserver, also if they don't have cache.
   5. **Authoritative nameserver** : The authoritative nameserver is usually the resolver’s last step in the journey for an IP address. The authoritative nameserver contains information specific to the domain name it serves (e.g. google.com) and it can provide a recursive resolver with the IP address. These are generally owned by the organizations that have bought the domain.
   6. Now, when you buy a domain from godaddy or any other website, they do the hosting for you. They basically act as the authoritative nameserver for the domain which you bought. You can also run your own authoritative server. 
   7. **DNS Registry** : The authoritative server contains the zone file containing the required resource records which is fetched from the distributed DNS database called the DNS registry. These are generally maintained by different organizations for different Top-level domains.

