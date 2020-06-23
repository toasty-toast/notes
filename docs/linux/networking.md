# Networking

## Check if a Port is Open and Accessible

If using Bash Shell, then you can use its feature to check if a port is open or closed:

```bash
$ (timeout 1 bash -c '</dev/tcp/127.0.0.1/17500 && echo PORT OPEN || echo PORT CLOSED') 2>/dev/null
PORT OPEN
$ (timeout 1 bash -c '</dev/tcp/127.0.0.1/7500 && echo PORT OPEN || echo PORT CLOSED') 2>/dev/null
PORT CLOSED
```