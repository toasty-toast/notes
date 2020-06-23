# Networking

## Check if a Port is Open and Accessible

If `netstat` is installed, you can use it to try and directly connect to the port.

``` bash
netstat <ip> <port>
```

If `netstat` is not installed, and you can't install it due to permission issues, you can connecting to the port using `bash` directly.

``` bash
$ (timeout 1 bash -c '</dev/tcp/<ip>/<port> && echo PORT OPEN || echo PORT CLOSED') 2>/dev/null
PORT OPEN
$ (timeout 1 bash -c '</dev/tcp/<ip>/<port> && echo PORT OPEN || echo PORT CLOSED') 2>/dev/null
PORT CLOSED
```
