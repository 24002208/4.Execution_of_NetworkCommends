# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
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

## Program
Server
```
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        hostname = c.recv(1024).decode('utf-8')
        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break
        response = ping(hostname, verbose=False, count=4)
        c.send(str(response).encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()
```

Client
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()
```

## Output

<img width="1903" height="1100" alt="4-1" src="https://github.com/user-attachments/assets/7d48addc-2bf0-4909-b7a6-e7db392a911c" />
<img width="1918" height="1097" alt="4-2" src="https://github.com/user-attachments/assets/22f1a895-70cf-478a-a451-2f122a7bd23b" />
<img width="1918" height="1087" alt="4-3" src="https://github.com/user-attachments/assets/8be32c2d-c28f-4c1c-ada5-3208220940d2" />
<img width="1915" height="1065" alt="4-4" src="https://github.com/user-attachments/assets/e89c9ef1-d92d-403e-b5dc-9489234afed3" />
<img width="1918" height="1103" alt="4-5" src="https://github.com/user-attachments/assets/902bbc7d-5191-48cc-86e5-b9e8108bb923" />
<img width="1917" height="967" alt="4-6" src="https://github.com/user-attachments/assets/e2847f51-5792-4c84-8500-989dcf8b8577" />


## Result
Thus Execution of Network commands Performed 
