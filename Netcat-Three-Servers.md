Using ncat to Access Elasticache via Bastion Host
===

```text
My Local Network        |AWS Network
server1 <-------------> |server2 <-------------> server3
                        |
```

### Scenario:
Imagine you are accessing Server 1, and you need to connect to an Elasticache instance (Server 3) located within an AWS network. Server 2 acts as the bastion host in the public subnet, providing the gateway to reach resources within the private network.

### Problem:
Elasticache is not directly accessible from outside the AWS network.

### Solution:
We can leverage `ncat` (netcat) on the bastion host (Server 2) to establish a connection to Elasticache (Server 3).

#### Command Syntax:
```sh
ncat -klvvnp 8000 -e "/bin/nc nonexistent.serverless.apne1.cache.amazonaws.com 6379"
```

### Explanation:

+ `ncat`: Launches netcat with specified options.
+ `-klvvnp 8000`: Opens netcat in listening mode (-k), verbose (-vv), and specifies the local port (-p 8000) to listen on.
+ `-e "/bin/nc nonexistent.serverless.apne1.cache.amazonaws.com 6379"`: Executes /bin/nc (netcat) to establish a connection to `nonexistent.serverless.apne1.cache.amazonaws.com` on port `6379`.

### Note:

+ Replace `nonexistent.serverless.apne1.cache.amazonaws.com` with the actual DNS endpoint of your Elasticache instance.
