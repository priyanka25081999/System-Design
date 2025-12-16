Most developers use Redis. Few understand how to stop it from crashing their database.

Caching seems simple: "If data is in cache, return it. If not, get from DB and set cache."

This works until you hit scale. Then you encounter the Three Cache Killers:

Cache Penetration
The Issue: Users request data that doesn't exist (e.g., ID -1). The cache misses, the DB misses. If an attacker automates this, your DB dies.
The Fix: Bloom Filters or caching "empty" results.

Cache Breakdown (Hot Key Expiry)
The Issue: A celebrity posts. 1M people view the profile. The cache key expires at 12:00:01. Instantly, 10k requests hit the DB before the cache refreshes.
The Fix: Mutex locks (only one thread queries DB) or logical expiration (soft deletes).

Cache Avalanche
The Issue: You restart the server, or many keys expire simultaneously.
The Fix: Add a "Jitter" (random noise) to your TTLs so keys don't expire at the exact same second.

System design is about handling the edge cases, not the happy path.
