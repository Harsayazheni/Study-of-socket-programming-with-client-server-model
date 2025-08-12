# Study-of-socket-programming-with-client-server-model

STUDY OF SOCKET PROGRAMMING AND CLIENT – SERVER MODE

EXP: 3

DATE:6.3.23

AIM:

To implement socket programming date and time display from client to
server using TCPSockets

ALGORITHM:

Server:

1. Create a server socket and bind it to port.
2. Listen for new connection and when a connection arrives, accept it.
3. Send server‟s date and time to the client.
4. Read client‟s IP address sent by the client.
5. Display the client details.
6. Repeat steps 2-5 until the server is terminated.
7. Close all streams.
8. Close the server socket.
9. Stop.

Client:

1. Create a client socket and connect it to the server‟s port number.
2. Retrieve its own IP address using built-in function.
3. Send its address to the server.
4. Display the date & time sent by the server.
5. Close the input and output streams.
6. Close the client socket.
7. Stop.

PROGRAM:

CLIENT:

```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

c, addr = s.accept()

address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}

while True:
    ip = c.recv(1024).decode().strip()
    if not ip:
        break
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

c.close()
s.close()
```

SERVER:

```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

print(s.getsockname())

s.send("165.165.80.80".encode())
print(s.recv(1024).decode())

s.send("acknowledgement recived from the server".encode())
s.close()
```

OUTPUT:

CLIENT:
![Screenshot from 2023-05-22 09-02-05](https://github.com/Harsayazheni/Study-of-socket-programming-with-client-server-model/assets/118708467/f154c1be-1f82-4b66-818e-59f93aceb405)

SERVER:
![Screenshot from 2023-05-22 09-02-20](https://github.com/Harsayazheni/Study-of-socket-programming-with-client-server-model/assets/118708467/a6658c0d-f72d-4e50-a015-20c30173f279)

RESULT:

Thus, the program to implement socket programming date and time display from client to
server using TCP Sockets was successfully executed.
