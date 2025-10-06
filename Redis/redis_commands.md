# Redis Commands Reference

Redis is an open-source, in-memory data structure store used as a database, cache, and message broker. It supports various data structures such as strings, hashes, lists, sets, sorted sets, bitmaps, hyperloglogs, geospatial indexes, and streams. This document provides a comprehensive reference to Redis commands, grouped by their functionality.

For the most up-to-date information, refer to the official Redis documentation at [https://redis.io/commands](https://redis.io/commands).

---

## Table of Contents

1. [Key Management Commands](#key-management-commands)
2. [String Commands](#string-commands)
3. [Hash Commands](#hash-commands)
4. [List Commands](#list-commands)
5. [Set Commands](#set-commands)
6. [Sorted Set Commands](#sorted-set-commands)
7. [HyperLogLog Commands](#hyperloglog-commands)
8. [Geospatial Commands](#geospatial-commands)
9. [Stream Commands](#stream-commands)
10. [Bitmap Commands](#bitmap-commands)
11. [Connection Management Commands](#connection-management-commands)
12. [Server Management Commands](#server-management-commands)
13. [Transaction Commands](#transaction-commands)
14. [Pub/Sub Commands](#pubsub-commands)
15. [Scripting Commands](#scripting-commands)
16. [Cluster Commands](#cluster-commands)

---

## Key Management Commands

These commands manage keys in Redis, including their creation, deletion, and metadata operations.

- **DEL key [key ...]**: Removes the specified key(s). Returns the number of keys removed.
- **DUMP key**: Returns a serialized version of the value stored at the specified key.
- **EXISTS key [key ...]**: Returns the number of keys that exist.
- **EXPIRE key seconds**: Sets a timeout (in seconds) on the key. After the timeout, the key is deleted.
- **EXPIREAT key timestamp**: Sets an expiration time (Unix timestamp) for the key.
- **EXPIRETIME key**: Returns the absolute expiration time (Unix timestamp) of the key.
- **KEYS pattern**: Returns all keys matching the given pattern.
- **MIGRATE host port key|"" destination-db timeout [COPY] [REPLACE] [AUTH password] [AUTH2 username password] [KEYS key [key ...]]**: Atomically transfers a key from one Redis instance to another.
- **MOVE key db**: Moves a key to another database.
- **OBJECT ENCODING key**: Returns the encoding used for the value stored at the key.
- **OBJECT FREQ key**: Returns the logarithmic access frequency of the key.
- **OBJECT IDLETIME key**: Returns the idle time of the key in seconds.
- **OBJECT REFCOUNT key**: Returns the reference count of the value stored at the key.
- **PERSIST key**: Removes the expiration from a key.
- **PEXPIRE key milliseconds**: Sets a timeout (in milliseconds) on the key.
- **PEXPIREAT key milliseconds-timestamp**: Sets an expiration time (Unix timestamp in milliseconds) for the key.
- **PTTL key**: Returns the remaining time to live of a key in milliseconds.
- **RANDOMKEY**: Returns a random key from the database.
- **RENAME key newkey**: Renames a key.
- **RENAMENX key newkey**: Renames a key only if the new key does not exist.
- **RESTORE key ttl serialized-value [REPLACE] [ABSTTL] [IDLETIME seconds] [FREQ frequency]**: Restores a key from a serialized value.
- **SCAN cursor [MATCH pattern] [COUNT count] [TYPE type]**: Iteratively scans the keyspace.
- **SORT key [BY pattern] [LIMIT offset count] [GET pattern [GET pattern ...]] [ASC|DESC] [ALPHA] [STORE destination]**: Sorts elements in a list, set, or sorted set.
- **TOUCH key [key ...]**: Updates the last access time of the specified keys.
- **TTL key**: Returns the remaining time to live of a key in seconds.
- **TYPE key**: Returns the type of the value stored at the key.
- **UNLINK key [key ...]**: Removes the specified key(s) asynchronously.

---

## String Commands

String commands operate on string values, which are the simplest data type in Redis.

- **APPEND key value**: Appends a value to the string stored at the key.
- **BITCOUNT key [start end [BYTE|BIT]]**: Counts the number of set bits in a string.
- **BITFIELD key [GET type offset] [SET type offset value] [INCRBY type offset increment] [OVERFLOW WRAP|SAT|FAIL]**: Performs arbitrary bitfield operations.
- **BITOP operation destkey key [key ...]**: Performs bitwise operations (AND, OR, XOR, NOT) between strings.
- **BITPOS key bit [start [end [BYTE|BIT]]]**: Returns the position of the first bit set to 1 or 0 in a string.
- **DECR key**: Decrements the integer value of a key by one.
- **DECRBY key decrement**: Decrements the integer value of a key by the given number.
- **GET key**: Returns the value of the key.
- **GETBIT key offset**: Returns the bit value at the specified offset.
- **GETDEL key**: Returns and deletes the value of the key.
- **GETEX key [EX seconds|PX milliseconds|EXAT timestamp|PXAT milliseconds-timestamp|PERSIST]**: Returns the value of the key with optional expiration.
- **GETRANGE key start end**: Returns a substring of the string stored at the key.
- **GETSET key value**: Sets the value of a key and returns its old value.
- **INCR key**: Increments the integer value of a key by one.
- **INCRBY key increment**: Increments the integer value of a key by the given number.
- **INCRBYFLOAT key increment**: Increments the float value of a key by the given amount.
- **MGET key [key ...]**: Returns the values of all specified keys.
- **MSET key value [key value ...]**: Sets multiple keys to their respective values.
- **MSETNX key value [key value ...]**: Sets multiple keys to their values if none of the keys exist.
- **PSETEX key milliseconds value**: Sets the value and expiration (in milliseconds) of a key.
- **SET key value [EX seconds|PX milliseconds|EXAT timestamp|PXAT milliseconds-timestamp|KEEPTTL] [NX|XX] [GET]**: Sets the value of a key with optional expiration and conditions.
- **SETBIT key offset value**: Sets or clears the bit at the specified offset.
- **SETEX key seconds value**: Sets the value and expiration (in seconds) of a key.
- **SETNX key value**: Sets the value of a key if it does not exist.
- **SETRANGE key offset value**: Overwrites part of the string at the key starting at the specified offset.
- **STRLEN key**: Returns the length of the string stored at the key.

---

## Hash Commands

Hash commands manage Redis hashes, which are maps between string fields and string values.

- **HDEL key field [field ...]**: Removes the specified fields from the hash.
- **HEXISTS key field**: Checks if a field exists in the hash.
- **HGET key field**: Returns the value of a field in the hash.
- **HGETALL key**: Returns all fields and values in the hash.
- **HINCRBY key field increment**: Increments the integer value of a field by the given number.
- **HINCRBYFLOAT key field increment**: Increments the float value of a field by the given amount.
- **HKEYS key**: Returns all field names in the hash.
- **HLEN key**: Returns the number of fields in the hash.
- **HMGET key field [field ...]**: Returns the values of the specified fields in the hash.
- **HMSET key field value [field value ...]**: Sets multiple fields in the hash (deprecated, use HSET).
- **HSET key field value [field value ...]**: Sets one or more fields in the hash.
- **HSETNX key field value**: Sets a field in the hash if it does not exist.
- **HSTRLEN key field**: Returns the length of the value associated with the field.
- **HVALS key**: Returns all values in the hash.
- **HSCAN key cursor [MATCH pattern] [COUNT count]**: Iteratively scans the fields in a hash.

---

## List Commands

List commands manage Redis lists, which are ordered collections of strings.

- **BLMOVE source destination LEFT|RIGHT LEFT|RIGHT timeout**: Atomically pops and pushes an element between lists, blocking until an element is available or timeout is reached.
- **BLMPOP timeout numkeys key [key ...] LEFT|RIGHT [COUNT count]**: Pops elements from multiple lists, blocking until available.
- **BLPOP key [key ...] timeout**: Removes and returns the first element from the first non-empty list, blocking until available.
- **BRPOP key [key ...] timeout**: Removes and returns the last element from the first non-empty list, blocking until available.
- **BRPOPLPUSH source destination timeout**: Pops the last element from one list and pushes it to another, blocking until available (deprecated).
- **LINDEX key index**: Returns the element at the specified index in the list.
- **LINSERT key BEFORE|AFTER pivot value**: Inserts a value before or after a pivot element in the list.
- **LLEN key**: Returns the length of the list.
- **LMOVE source destination LEFT|RIGHT LEFT|RIGHT**: Atomically pops and pushes an element between lists.
- **LMPOP numkeys key [key ...] LEFT|RIGHT [COUNT count]**: Pops elements from multiple lists.
- **LPOP key [count]**: Removes and returns the first element(s) of the list.
- **LPOS key element [RANK rank] [COUNT count] [MAXLEN len]**: Returns the index of an element in the list.
- **LPUSH key element [element ...]**: Prepends one or more elements to the list.
- **LPUSHX key element [element ...]**: Prepends elements to the list if it exists.
- **LRANGE key start stop**: Returns a range of elements from the list.
- **LREM key count element**: Removes occurrences of an element from the list.
- **LSET key index element**: Sets the element at the specified index in the list.
- **LTRIM key start stop**: Trims the list to the specified range.
- **RPOP key [count]**: Removes and returns the last element(s) of the list.
- **RPOPLPUSH source destination**: Pops the last element from one list and pushes it to another (deprecated).
- **RPUSH key element [element ...]**: Appends one or more elements to the list.
- **RPUSHX key element [element ...]**: Appends elements to the list if it exists.

---

## Set Commands

Set commands manage Redis sets, which are unordered collections of unique strings.

- **SADD key member [member ...]**: Adds one or more members to a set.
- **SCARD key**: Returns the cardinality (number of members) of the set.
- **SDIFF key [key ...]**: Returns the difference between the first set and all subsequent sets.
- **SDIFFSTORE destination key [key ...]**: Stores the difference between sets in a new set.
- **SINTER key [key ...]**: Returns the intersection of multiple sets.
- **SINTERSTORE destination key [key ...]**: Stores the intersection of sets in a new set.
- **SISMEMBER key member**: Checks if a member exists in the set.
- **SMISMEMBER key member [member ...]**: Checks if multiple members exist in the set.
- **SMEMBERS key**: Returns all members of the set.
- **SMOVE source destination member**: Moves a member from one set to another.
- **SPOP key [count]**: Removes and returns random member(s) from the set.
- **SRANDMEMBER key [count]**: Returns random member(s) from the set without removing them.
- **SREM key member [member ...]**: Removes one or more members from the set.
- **SSCAN key cursor [MATCH pattern] [COUNT count]**: Iteratively scans the members of a set.
- **SUNION key [key ...]**: Returns the union of multiple sets.
- **SUNIONSTORE destination key [key ...]**: Stores the union of sets in a new set.

---

## Sorted Set Commands

Sorted set commands manage Redis sorted sets, which are sets with associated scores for ordering.

- **ZADD key [NX|XX] [GT|LT] [CH] [INCR] score member [score member ...]**: Adds members to a sorted set with their scores.
- **ZCARD key**: Returns the cardinality of the sorted set.
- **ZCOUNT key min max**: Counts members with scores within the given range.
- **ZDIFF numkeys key [key ...] [WITHSCORES]**: Returns the difference between sorted sets.
- **ZDIFFSTORE destination numkeys key [key ...]**: Stores the difference between sorted sets.
- **ZINCRBY key increment member**: Increments the score of a member.
- **ZINTER numkeys key [key ...] [WEIGHTS weight [weight ...]] [AGGREGATE SUM|MIN|MAX] [WITHSCORES]**: Returns the intersection of sorted sets.
- **ZINTERSTORE destination numkeys key [key ...] [WEIGHTS weight [weight ...]] [AGGREGATE SUM|MIN|MAX]**: Stores the intersection of sorted sets.
- **ZLEXCOUNT key min max**: Counts members in a lexicographical range.
- **ZMPOP numkeys key [key ...] MIN|MAX [COUNT count]**: Pops members with the highest or lowest scores.
- **ZMSCORE key member [member ...]**: Returns the scores of the specified members.
- **ZPOPMAX key [count]**: Removes and returns members with the highest scores.
- **ZPOPMIN key [count]**: Removes and returns members with the lowest scores.
- **ZRANDMEMBER key [count [WITHSCORES]]**: Returns random members from the sorted set.
- **ZRANGE key start stop [BYSCORE|BYLEX] [REV] [LIMIT offset count] [WITHSCORES]**: Returns a range of members.
- **ZRANGESTORE dst src min max [BYSCORE|BYLEX] [REV] [LIMIT offset count]**: Stores a range of members in a new sorted set.
- **ZRANK key member**: Returns the rank of a member in the sorted set.
- **ZREM key member [member ...]**: Removes members from the sorted set.
- **ZREMRANGEBYLEX key min max**: Removes members in a lexicographical range.
- **ZREMRANGEBYRANK key start stop**: Removes members by rank.
- **ZREMRANGEBYSCORE key min max**: Removes members by score range.
- **ZREVRANK key member**: Returns the reverse rank of a member.
- **ZSCAN key cursor [MATCH pattern] [COUNT count]**: Iteratively scans the sorted set.
- **ZUNION numkeys key [key ...] [WEIGHTS weight [weight ...]] [AGGREGATE SUM|MIN|MAX] [WITHSCORES]**: Returns the union of sorted sets.
- **ZUNIONSTORE destination numkeys key [key ...] [WEIGHTS weight [weight ...]] [AGGREGATE SUM|MIN|MAX]**: Stores the union of sorted sets.

---

## HyperLogLog Commands

HyperLogLog commands manage probabilistic data structures for estimating cardinality.

- **PFADD key element [element ...]**: Adds elements to a HyperLogLog.
- **PFCOUNT key [key ...]**: Returns the estimated cardinality of the HyperLogLog(s).
- **PFMERGE destkey sourcekey [sourcekey ...]**: Merges multiple HyperLogLogs into one.

---

## Geospatial Commands

Geospatial commands manage geospatial indexes for location-based data.

- **GEOADD key [NX|XX] [CH] longitude latitude member [longitude latitude member ...]**: Adds geospatial items to a key.
- **GEODIST key member1 member2 [unit]**: Returns the distance between two members.
- **GEOHASH key member [member ...]**: Returns the Geohash strings of members.
- **GEOPOS key member [member ...]**: Returns the positions (longitude, latitude) of members.
- **GEORADIUS key longitude latitude radius unit [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count [ANY]] [ASC|DESC] [STORE storekey] [STOREDIST storekey]**: Returns members within a radius (deprecated).
- **GEORADIUSBYMEMBER key member radius unit [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count [ANY]] [ASC|DESC] [STORE storekey] [STOREDIST storekey]**: Returns members within a radius from a member (deprecated).
- **GEOSEARCH key [FROMMEMBER member | FROMLONLAT longitude latitude] [BYRADIUS radius unit | BYBOX width height unit] [ASC|DESC] [COUNT count [ANY]] [WITHCOORD] [WITHDIST] [WITHHASH]**: Searches for members in a geospatial index.
- **GEOSEARCHSTORE destination source [FROMMEMBER member | FROMLONLAT longitude latitude] [BYRADIUS radius unit | BYBOX width height unit] [ASC|DESC] [COUNT count [ANY]] [STOREDIST]**: Stores the results of a geospatial search.

---

## Stream Commands

Stream commands manage Redis streams, which are append-only logs for time-series data.

- **XACK key group id [id ...]**: Acknowledges messages in a consumer group.
- **XADD key [NOMKSTREAM] [MAXLEN|MINID [=|~] threshold [LIMIT count]] id field value [field value ...]**: Adds a message to a stream.
- **XAUTOCLAIM key group consumer min-idle-time start [COUNT count] [JUSTID]**: Claims pending messages automatically.
- **XCLAIM key group consumer min-idle-time id [id ...] [IDLE ms] [TIME ms-unix-time] [RETRYCOUNT count] [FORCE] [JUSTID]**: Claims pending messages.
- **XDEL key id [id ...]**: Deletes messages from a stream.
- **XGROUP CREATE key groupname id|$ [MKSTREAM] [ENTRIESREAD entries_read]**: Creates a consumer group.
- **XGROUP CREATECONSUMER key groupname consumername**: Creates a consumer in a group.
- **XGROUP DELCONSUMER key groupname consumername**: Deletes a consumer from a group.
- **XGROUP DESTROY key groupname**: Destroys a consumer group.
- **XGROUP SETID key groupname id|$ [ENTRIESREAD entries_read]**: Sets the last delivered ID for a consumer group.
- **XINFO CONSUMERS key groupname**: Returns information about consumers in a group.
- **XINFO GROUPS key**: Returns information about consumer groups.
- **XINFO STREAM key [FULL [COUNT count]]**: Returns detailed information about a stream.
- **XLEN key**: Returns the number of entries in a stream.
- **XPENDING key group [IDLE min-idle-time] [start end count] [consumer]**: Returns pending entries in a consumer group.
- **XRANGE key start end [COUNT count]**: Returns entries in a stream within a range.
- **XREAD [COUNT count] [BLOCK milliseconds] STREAMS key [key ...] id [id ...]**: Reads entries from one or more streams.
- **XREADGROUP GROUP group consumer [COUNT count] [BLOCK milliseconds] [NOACK] STREAMS key [key ...] id [id ...]**: Reads entries from streams for a consumer group.
- **XREVRANGE key end start [COUNT count]**: Returns entries in a stream in reverse order.
- **XTRIM key MAXLEN|MINID [=|~] threshold [LIMIT count]**: Trims a stream to a maximum length or minimum ID.

---

## Bitmap Commands

Bitmap commands operate on strings as bit arrays.

- **BITCOUNT key [start end [BYTE|BIT]]**: Counts set bits in a string (also listed under String Commands).
- **BITFIELD key [GET type offset] [SET type offset value] [INCRBY type offset increment] [OVERFLOW WRAP|SAT|FAIL]**: Performs bitfield operations (also listed under String Commands).
- **BITOP operation destkey key [key ...]**: Performs bitwise operations (also listed under String Commands).
- **BITPOS key bit [start [end [BYTE|BIT]]]**: Finds the first bit set to 1 or 0 (also listed under String Commands).

---

## Connection Management Commands

These commands manage client connections to the Redis server.

- **AUTH [username] password**: Authenticates the connection.
- **CLIENT CACHING YES|NO**: Enables or disables tracking for key changes.
- **CLIENT GETNAME**: Returns the name of the current connection.
- **CLIENT GETREDIR**: Returns the tracking redirection address.
- **CLIENT ID**: Returns the unique ID of the current connection.
- **CLIENT INFO**: Returns information about the current client connection.
- **CLIENT KILL [ip:port] [ID client-id] [TYPE normal|master|replica|pubsub] [USER username] [ADDR ip:port] [LADDR ip:port] [SKIPME yes/no]**: Kills client connections.
- **CLIENT LIST [TYPE normal|master|replica|pubsub] [ID client-id [client-id ...]]**: Lists all client connections.
- **CLIENT PAUSE timeout [WRITE|ALL]**: Suspends client commands for the specified duration.
- **CLIENT REPLY ON|OFF|SKIP**: Controls server responses to commands.
- **CLIENT SETNAME name**: Sets the name of the current connection.
- **CLIENT TRACKING ON|OFF [REDIRECT client-id] [PREFIX prefix [prefix ...]] [BCAST] [OPTIN] [OPTOUT] [NOLOOP]**: Enables or disables client tracking.
- **CLIENT UNBLOCK client-id [TIMEOUT|ERROR]**: Unblocks a client.
- **ECHO message**: Returns the specified message.
- **HELLO protover [AUTH username password] [SETNAME clientname]**: Switches to a specific protocol version.
- **PING [message]**: Checks if the server is reachable.
- **QUIT**: Closes the connection.
- **SELECT index**: Selects the database to use.

---

## Server Management Commands

These commands manage the Redis server itself.

- **ACL CAT [categoryname]**: Lists ACL categories or commands in a category.
- **ACL DELUSER username [username ...]**: Deletes ACL users.
- **ACL DRYRUN username command [arg [arg ...]]**: Simulates command execution for an ACL user.
- **ACL GENPASS [bits]**: Generates a random password.
- **ACL GETUSER username**: Returns details about an ACL user.
- **ACL LIST**: Lists all ACL rules.
- **ACL LOAD**: Loads ACLs from the configuration file.
- **ACL LOG [count|RESET]**: Lists or resets the ACL log.
- **ACL SAVE**: Saves ACLs to the configuration file.
- **ACL SETUSER username [rule [rule ...]]**: Creates or modifies an ACL user.
- **ACL USERS**: Lists all ACL usernames.
- **ACL WHOAMI**: Returns the current ACL username.
- **BGREWRITEAOF**: Asynchronously rewrites the append-only file.
- **BGSAVE [SCHEDULE]**: Asynchronously saves the dataset to disk.
- **COMMAND**: Returns details about all Redis commands.
- **COMMAND COUNT**: Returns the total number of commands.
- **COMMAND GETKEYS command [arg [arg ...]]**: Extracts keys from a command.
- **COMMAND INFO command-name [command-name ...]**: Returns details about specific commands.
- **CONFIG GET parameter [parameter ...]**: Gets configuration parameters.
- **CONFIG RESETSTAT**: Resets server statistics.
- **CONFIG REWRITE**: Rewrites the configuration file with the current configuration.
- **CONFIG SET parameter value [parameter value ...]**: Sets configuration parameters.
- **DBSIZE**: Returns the number of keys in the current database.
- **FAILOVER [TO host port [FORCE]] [ABORT] [TIMEOUT milliseconds]**: Initiates a failover to a replica.
- **FLUSHALL [ASYNC|SYNC]**: Deletes all keys in all databases.
- **FLUSHDB [ASYNC|SYNC]**: Deletes all keys in the current database.
- **INFO [section]**: Returns information about the server.
- **LASTSAVE**: Returns the Unix timestamp of the last successful save.
- **LATENCY DOCTOR**: Provides a latency diagnostics report.
- **LATENCY GRAPH event**: Generates a latency graph for an event.
- **LATENCY HISTORY event**: Returns the latency history for an event.
- **LATENCY LATEST**: Returns the latest latency events.
- **LATENCY RESET [event [event ...]]**: Resets latency data.
- **MEMORY DOCTOR**: Provides a memory diagnostics report.
- **MEMORY MALLOC-STATS**: Returns memory allocator statistics.
- **MEMORY PURGE**: Frees memory used by the allocator.
- **MEMORY STATS**: Returns memory usage statistics.
- **MEMORY USAGE key [SAMPLES count]**: Estimates memory usage of a key.
- **MODULE LIST**: Lists loaded modules.
- **MODULE LOAD path [arg [arg ...]]**: Loads a module.
- **MODULE UNLOAD name**: Unloads a module.
- **MONITOR**: Streams back every command processed by the server.
- **PSYNC replicationid offset**: Initiates replication sync (internal command).
- **REPLCONF**: Configures replication parameters (internal command).
- **REPLICAOF host port**: Makes the server a replica of another instance or promotes it to master.
- **ROLE**: Returns the role of the server (master, replica, etc.).
- **SAVE**: Synchronously saves the dataset to disk.
- **SHUTDOWN [NOSAVE|SAVE] [NOW] [FORCE] [ABORT]**: Stops the server.
- **SLOWLOG GET [count]**: Returns entries from the slow log.
- **SLOWLOG LEN**: Returns the length of the slow log.
- **SLOWLOG RESET**: Resets the slow log.
- **SWAPDB index1 index2**: Swaps two databases.
- **SYNC**: Initiates full replication sync (internal command).
- **TIME**: Returns the current server time.

---

## Transaction Commands

Transaction commands manage atomic execution of multiple commands.

- **DISCARD**: Discards all commands in a transaction.
- **EXEC**: Executes all commands in a transaction.
- **MULTI**: Marks the start of a transaction.
- **UNWATCH**: Forgets all watched keys.
- **WATCH key [key ...]**: Watches keys for conditional transactions.

---

## Pub/Sub Commands

Pub/Sub commands manage the publish/subscribe messaging paradigm.

- **PSUBSCRIBE pattern [pattern ...]**: Subscribes to channels matching a pattern.
- **PUBLISH channel message**: Publishes a message to a channel.
- **PUBSUB CHANNELS [pattern]**: Lists active channels.
- **PUBSUB NUMPAT**: Returns the number of unique patterns subscribed to.
- **PUBSUB NUMSUB [channel [channel ...]]**: Returns the number of subscribers for channels.
- **PUNSUBSCRIBE [pattern [pattern ...]]**: Unsubscribes from patterns.
- **SUBSCRIBE channel [channel ...]**: Subscribes to channels.
- **UNSUBSCRIBE [channel [channel ...]]**: Unsubscribes from channels.

---

## Scripting Commands

Scripting commands manage Lua scripts in Redis.

- **EVAL script numkeys key [key ...] arg [arg ...]**: Executes a Lua script.
- **EVALSHA sha1 numkeys key [key ...] arg [arg ...]**: Executes a Lua script by its SHA1 hash.
- **SCRIPT DEBUG YES|SYNC|NO**: Sets the script debugging mode.
- **SCRIPT EXISTS sha1 [sha1 ...]**: Checks if scripts exist in the script cache.
- **SCRIPT FLUSH [ASYNC|SYNC]**: Removes all scripts from the cache.
- **SCRIPT KILL**: Kills the currently executing script.
- **SCRIPT LOAD script**: Loads a script into the cache and returns its SHA1 hash.

---

## Cluster Commands

Cluster commands manage Redis Cluster, a distributed implementation of Redis.

- **CLUSTER ADDSLOTS slot [slot ...]**: Assigns slots to the current node.
- **CLUSTER BUMPEPOCH**: Advances the cluster config epoch.
- **CLUSTER COUNT-FAILURE-REPORTS node-id**: Returns the number of failure reports for a node.
- **CLUSTER COUNTKEYSINSLOT slot**: Returns the number of keys in a slot.
- **CLUSTER DELSLOTS slot [slot ...]**: Removes slots from the current node.
- **CLUSTER FAILOVER [FORCE|TAKEOVER]**: Initiates a manual failover.
- **CLUSTER FORGET node-id**: Removes a node from the nodes table.
- **CLUSTER GETKEYSINSLOT slot count**: Returns keys in a slot.
- **CLUSTER INFO**: Returns information about the cluster state.
- **CLUSTER KEYSLOT key**: Returns the hash slot for a key.
- **CLUSTER MEET ip port**: Connects to a node to join the cluster.
- **CLUSTER NODES**: Returns the cluster configuration.
- **CLUSTER REPLICAS node-id**: Lists replicas of a node.
- **CLUSTER REPLICATE node-id**: Configures the current node as a replica.
- **CLUSTER RESET [HARD|SOFT]**: Resets the cluster state.
- **CLUSTER SAVECONFIG**: Saves the cluster configuration to disk.
- **CLUSTER SET-CONFIG-EPOCH config-epoch**: Sets the config epoch for a node.
- **CLUSTER SETSLOT slot IMPORTING|MIGRATING|STABLE|NODE node-id**: Manages slot ownership.
- **CLUSTER SLAVES node-id**: Lists slaves of a node (deprecated, use CLUSTER REPLICAS).
- **CLUSTER SLOTS**: Returns the slot-to-node mappings.
- **READONLY**: Enables read-only mode for cluster connections.
- **READWRITE**: Disables read-only mode for cluster connections.

---

## Notes

- Some commands (e.g., `BRPOPLPUSH`, `RPOPLPUSH`, `HMSET`, `GEORADIUS`, `GEORADIUSBYMEMBER`) are deprecated in newer Redis versions. Use their replacements where applicable (e.g., `LMOVE` for `BRPOPLPUSH` and `RPOPLPUSH`, `HSET` for `HMSET`, `GEOSEARCH` for `GEORADIUS` and `GEORADIUSBYMEMBER`).
- Commands like `PSYNC`, `SYNC`, and `REPLCONF` are internal and typically not used directly by clients.
- For detailed usage, arguments, and examples, refer to the official Redis documentation.

This reference covers Redis commands up to the latest stable version as of October 2025. Always check [https://redis.io/commands](https://redis.io/commands) for the most current information.