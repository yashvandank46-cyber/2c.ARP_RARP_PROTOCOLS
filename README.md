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
## PROGRAM - ARP

## SERVER

```py
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
## CLIENT

```py
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP
<img width="830" height="102" alt="Screenshot 2026-08-25 101029" src="https://github.com/user-attachments/assets/007479f2-805d-4917-b8ac-636ab1fcef6f" />

<img width="822" height="162" alt="Screenshot 2026-08-25 101234" src="https://github.com/user-attachments/assets/d5e4509e-437b-4fb6-bf87-999ad75e162d" />


## PROGRAM - RARP

## SERVER

```py
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

## CLIENT 

```py
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP

<img width="835" height="103" alt="Screenshot 2026-08-25 102140" src="https://github.com/user-attachments/assets/b15c9164-bb88-46d9-8584-b42ee86b160a" />


<img width="828" height="163" alt="Screenshot 2026-08-25 102153" src="https://github.com/user-attachments/assets/a1f087dc-d80f-4ed2-bf9b-55bc212d4da6" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.






