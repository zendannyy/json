
SSH tunneling aka ssh port forearding
- Using an existing ssh connection for transporting traffic in an arbitrary manner
- Usually used to move data over encryted ssh connection

## Local Port Forwarding
client traffic -> SSH Connection -> Redirect to dest host/port specified 
i.e using a compromised server to build an ssh tunnel in order to talk to db

```ssh -L localport:db:remoteport username@server```
from ssh man page
     -L [bind_address:]port:host:hostport
     -L [bind_address:]port:remote_socket
     -L local_socket:host:hostport


## Remote Port Forwarding
server traffic -> SSH connection to client -> Redirect to dest host/port specified 

```ssh -R remoteport:db:localport username@server```
from ssh man page
     -R [bind_address:]port:host:hostport
     -R [bind_address:]port:local_socket
     -R remote_socket:host:hostport
     -R remote_socket:local_socket


## Dynamic Port Forwarding
Traffic from client SSH tunnel sends it to the server which acts as dynamic proxy. The SSH connection will act as a SOCKS server.
The Traffic appears to be coming from the host where the SOCKS server is listening and does not show the IP address of the host that initiated the request, therefore stealthy. 

```ssh -D port username@server```


## References 
[SpecterOps Tunneling Guide](https://posts.specterops.io/offensive-security-guide-to-ssh-tunnels-and-proxies-b525cbd4d4c6)
[SSH Academy](https://www.ssh.com/academy/ssh/tunneling)