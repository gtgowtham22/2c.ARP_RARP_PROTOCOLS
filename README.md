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
## PROGRAM 
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))
print("Connected to the server.")

while True:
    ip = input("Enter logical Address (or type 'exit' to quit): ")
    if ip.lower() == 'exit':
        print("Closing connection.")
        break
    s.send(ip.encode())
    mac_address = s.recv(1024).decode()
    print("MAC Address:", mac_address)

s.close()
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server is listening...")

c, addr = s.accept()
print(f"Connection established with {addr}")

address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}

while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

```

## OUPUT 
![idle 3rd server](https://github.com/user-attachments/assets/3e22865e-9b3f-4112-8b75-3ab524aa0949)
![idle 3rd client](https://github.com/user-attachments/assets/5a9a7115-9cab-48c1-99d9-007fe01cf4ec)
![cmd 3rd server](https://github.com/user-attachments/assets/25e862af-cb79-47c2-8712-29bfda41eace)
![cmd 3rd client](https://github.com/user-attachments/assets/d3df3ab3-894f-4582-b249-d8f73bd8ac84)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
