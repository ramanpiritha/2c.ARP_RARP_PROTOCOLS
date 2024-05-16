# Name: Piritharaman R
# Ref no: 212223230148

# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
```
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
```
## Server:
```
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
```
## PROGRAM - ARP
# Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode())
```
# Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
# Client
![arp client](https://github.com/ramanpiritha/2c.ARP_RARP_PROTOCOLS/assets/147084116/22dd04aa-4496-4215-a85c-33fb16c79e7b)
# Server
![arp server](https://github.com/ramanpiritha/2c.ARP_RARP_PROTOCOLS/assets/147084116/1f2b8a3b-822c-4e1e-9cc6-51c22246b545)

## PROGRAM - RARP
# Client:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode())
```
# Server:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
# Client
![rarp client](https://github.com/ramanpiritha/2c.ARP_RARP_PROTOCOLS/assets/147084116/c3f61461-1754-4c00-abe1-cb9b1152f6af)

# Server
![rarp server](https://github.com/ramanpiritha/2c.ARP_RARP_PROTOCOLS/assets/147084116/4cffe9b2-4f17-44cb-9ea5-33fb1fa18340)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
