# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
## server
```python

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter Logical Address : ")
    s.send(ip.encode())
    print("Mac Address : ",s.recv(1024).decode())
```
## client 
```python
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"68:34:21:98:46:99":"192.168.252.52"}
while True:
    ip=c.recv(1024).decode()
    try:
     c.send(address[ip].encode())
    except KeyError:
     c.send("Not Found".encode())
```

## OUPUT - ARP
<img width="1033" height="375" alt="image" src="https://github.com/user-attachments/assets/3a98722b-f0f1-482a-8618-ceabad1d7019" />

## PROGRAM - RARP
## server
```python

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address : ",s.recv(1024).decode())
```
## client
```python
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"68:34:21:98:46:99":"192.168.252.52"}
while True:
    ip=c.recv(1024).decode()
    try:
     c.send(address[ip].encode())
    except KeyError:
     c.send("Not Found".encode())
```
## OUPUT -RARP
<img width="1032" height="437" alt="image" src="https://github.com/user-attachments/assets/22447180-6d3f-41de-a637-653480e1fbd9" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
