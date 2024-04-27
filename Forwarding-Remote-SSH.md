SSH Remote Port Forwarding
===

### Introduction:
SSH port forwarding allows users to securely access services running on a remote server as if they were running locally on their machine. This is particularly useful for scenarios where services are only accessible on the remote server's localhost.

### Example Scenario:
Imagine we have a PostgreSQL database running on a remote host (RHOST), and it's only accessible on `127.0.0.1:5432` on that server. If we need to access this database from our local machine, SSH port forwarding comes to the rescue.

---

#### Command Syntax:
```sh
ssh -i key-file -L 127.0.0.1:LPORT:127.0.0.1:RPORT -C -N -l RUSER RHOST
```

Flags:

+ -i identity_file: Specifies the identity (private key) file for authentication.
+ -L LHOST:LPORT:RHOST:RPORT: Specifies the local and remote port forwarding configuration.
+ -C: Requests compression of all data for improved performance.
+ -N: Prevents execution of a remote command, useful for port forwarding only.
+ -l login_name: Specifies the username for logging into the remote server.

---
