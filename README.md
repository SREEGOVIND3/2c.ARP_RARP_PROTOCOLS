# 2c.SIMULATING ARP /RARP PROTOCOLS
## NAME : SREE GOVIND SA
## REG NO:212224240159
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
## CLIENT:
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
## SERVER: 
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
![2c1](https://github.com/user-attachments/assets/a7232f39-19ae-4e6e-8193-8aacbc0f6c6f)
![2c1 2](https://github.com/user-attachments/assets/71553a0e-333b-4ef3-bf73-86705e2b1aaf)
## PROGRAM - RARP
## CLIENT:
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
## SERVER: 
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
![2bpic](https://github.com/user-attachments/assets/4324f58f-b4fe-437a-b445-39b5531a670c)
![2bpic1](https://github.com/user-attachments/assets/df59444d-86ee-4dbc-aadd-1be25b5332b6)
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
