# 4.Execution_of_NetworkCommands
## AIM :
Use of Network commands in Real Time environment
## Software :
Command Prompt And Network Protocol Analyzer
## Procedure: 
To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

## Program:
### Client:
```
from pythonping import ping
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
while True:
    c,addr=s.accept()
    print("Connecting from ",addr)
    try:
        hostname=c.recv(1024).decode().strip()
        if hostname:
            try:
                response=str(ping(hostname,verbose=True))
                c.send(response.encode())
            except Exception as e:
                c.send("ping failed  {}".format(e).encode())
        else:
            c.send("Hostname not provided".encode())
    except Exception as e:
        print("Error: ",e)
    finally:
        c.close()
```
### Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
try:
    while True:
        ip= input("Enter Website u want to ping :")
        s.send(ip.encode())
        response=s.recv(1024).decode()
        if response:
            print ("Ping result :",response)
        else:
            print ("No response from server")
except Exception as e:
    print ("Error:", e)
finally:
    s.close()
```
### Traceroute command:
```
target = ["www.google.com"] 
result, unans = traceroute(target,maxttl=32) 
print(result,unans)
```

## Output
### Client:
![323099466-8db6ea32-232e-4e4d-9cb8-17fe28905f80](https://github.com/s-adhithya/4.Execution_of_NetworkCommends/assets/113497423/1fe9208d-b53e-460a-a7c9-f0cea8f9ed01)
### Server:
![323100013-cc32b8eb-957c-4693-b025-9aa40d34bf97](https://github.com/s-adhithya/4.Execution_of_NetworkCommends/assets/113497423/4c99f1e0-a714-407f-8cf5-78f977316419)
### Traceroute command:
![323100630-a3a76774-1fc5-453b-a0fe-b1bd35d1595a](https://github.com/s-adhithya/4.Execution_of_NetworkCommends/assets/113497423/ec2c6fe7-370d-4e14-85fb-8d87d106756d)

## Result
Thus Execution of Network commands Performed 
