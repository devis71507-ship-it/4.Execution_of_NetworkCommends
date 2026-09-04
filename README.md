# 4.Execution_of_NetworkCommands
## AIM :
    Use of Network commands in Real Time environment
## Software :
    Command Prompt And Network Protocol Analyzer
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

SEVER.PY:

```
import socket

s = socket.socket()
s.bind(("localhost", 8081))
s.listen(1)

print("Server running...")

while True:
    c, addr = s.accept()

    request = c.recv(1024).decode()
    print("Request received")

    if "GET" in request:
        f = open("index.html", "r")
        data = f.read()
        f.close()

        response = "HTTP/1.1 200 OK\n\n" + data
        c.send(response.encode())

    elif "POST" in request:
        data = request.split("\n\n")[1]

        f = open("upload.txt", "w")
        f.write(data)
        f.close()

        c.send("HTTP/1.1 200 OK\n\nFile Uploaded".encode())

    c.close()
```

CLIENT.PY:

```
import socket

s = socket.socket()
s.connect(("localhost", 8081))

ch = input("1. Download  2. Upload : ")

if ch == "1":
    req = "GET / HTTP/1.1\nHost: localhost\n\n"
    s.send(req.encode())

    data = s.recv(4096)
    print(data.decode())

elif ch == "2":
    msg = input("Enter data to upload: ")

    req = "POST / HTTP/1.1\nHost: localhost\n\n" + msg
    s.send(req.encode())

    data = s.recv(1024)
    print(data.decode())

else:
    print("Invalid choice")

s.close()
```

## Output

<img width="1180" height="257" alt="Screenshot 2026-09-03 135051" src="https://github.com/user-attachments/assets/111d8c5d-f3b7-4adc-b552-d0365c7e5619" />

<img width="1375" height="303" alt="Screenshot 2026-09-03 135107" src="https://github.com/user-attachments/assets/1f5332a8-78c1-4fcb-a448-33ba4c47e670" />

## Result
Thus Execution of Network commands Performed 
