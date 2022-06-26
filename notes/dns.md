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
   3. **Root nameservers** : 
