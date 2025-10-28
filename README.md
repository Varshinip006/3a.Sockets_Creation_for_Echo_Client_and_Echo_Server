# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS
# AIM
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.
## PROGRAM
Server
```
import socket
s = socket.socket()
try:
    s.bind(('localhost', 8000))
except OSError:
    s.bind(('localhost', 0))  
host, port = s.getsockname()
print(f"Server is running on {host}:{port}")
with open("port.txt", "w") as f:
    f.write(str(port))
s.listen(5)
print("Waiting for client connection...")
c, addr = s.accept()
print("Connected with", addr)
while True:
    client_message = c.recv(1024).decode()
    if not client_message:
        break
    print("Client >", client_message)
    c.send(client_message.encode())
c.close()

```
Client
```
import socket
s = socket.socket()
with open("port.txt", "r") as f:
    port = int(f.read().strip())
s.connect(('localhost', port))
print(f"Connected to server on port {port}")

while True:
    msg = input("Client > ")
    if msg.lower() == 'exit':
        print("Closing connection...")
        s.close()
        break
    s.send(msg.encode())
    print("Server >", s.recv(1024).decode())
```
## OUPUT

Server
<img width="1175" height="223" alt="image" src="https://github.com/user-attachments/assets/4cdb3f16-c73d-4a07-8220-47b57f7e641c" />

Client
<img width="1219" height="300" alt="image" src="https://github.com/user-attachments/assets/f4cbf85b-3a7a-44dd-a2cc-d525f8ec9222" />


## RESULT
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
