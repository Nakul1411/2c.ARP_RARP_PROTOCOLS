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
Client

socket 
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
Server

import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
     ip=input("Enter logical Address : ") 
     s.send(ip.encode()) 
     print("MAC Address",s.recv(1024).decode())
## OUPUT - ARP
![Screenshot 2024-11-16 125224](https://github.com/user-attachments/assets/6e65b050-58eb-4a79-9fcf-73651bf21d57)
![Screenshot 2024-11-16 125233](https://github.com/user-attachments/assets/e83da409-a8cc-4653-a023-6e2e7ba9834d)

## PROGRAM - RARP
Client

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

  Server

import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
## OUPUT -RARP
![Screenshot 2024-11-16 125348](https://github.com/user-attachments/assets/eeb092ed-7e57-4542-abad-7d896a189f63)
![Screenshot 2024-11-16 125356](https://github.com/user-attachments/assets/8fe1e27e-37fc-4255-a046-2eb242ac7271)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
