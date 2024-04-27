SSH Local Port Forwarding (Reverse SSH Tunneling) 
===

### Introduction:
Local port forwarding, also known as reverse SSH tunneling, enables users to securely expose services running on their local machine to a remote server. This technique is beneficial in scenarios where the local machine is behind a firewall, NAT, or otherwise inaccessible from the internet.

### Example Scenario:
Suppose we have a web server running locally on our machine (LHOST) on port 8080, and we want to make it accessible from a remote server (RHOST). Using local port forwarding, we can securely tunnel traffic from the remote server's port to our local machine's service.

---

#### Command Syntax:
```sh
ssh -i key-file -R RHOST:RPORT:LHOST:LPORT -C -N -l RUSER RHOST
```

Flags:

+ `-i` identity_file: Specifies the identity (private key) file for authentication.
+ `-R` RHOST:RPORT:LHOST:LPORT: Specifies the remote and local port forwarding configuration. Traffic sent to RHOST:RPORT on the remote server is forwarded to LHOST:LPORT on the local machine.
+ `-C` Requests compression of all data for improved performance.
+ `-N` Prevents execution of a remote command, useful for port forwarding only.
+ `-l` `login_name`: Specifies the username for logging into the remote server.

---
