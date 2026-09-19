# Exercise 4: To Implement Socket Programming Using TCP/UDP

```
Name : Namachivayam T
Reg No : 212223060179
```

## Aim

To implement socket programming using TCP and UDP protocols for communication between a client and a server.

## Algorithm

### TCP Socket Programming

**Server Side:**

1. Start the program.
2. Create a TCP socket using `SOCK_STREAM`.
3. Bind the socket to an IP address and port number.
4. Listen for incoming client connections.
5. Accept the client connection.
6. Receive data from the client.
7. Send a response to the client.
8. Close the connection and socket.
9. Stop the program.

**Client Side:**

1. Start the program.
2. Create a TCP socket.
3. Connect to the server using its IP address and port number.
4. Send data to the server.
5. Receive the server's response.
6. Display the received message.
7. Close the socket.
8. Stop the program.

### UDP Socket Programming

**Server Side:**

1. Start the program.
2. Create a UDP socket using `SOCK_DGRAM`.
3. Bind the socket to an IP address and port number.
4. Receive data from the client using `recvfrom()`.
5. Send a response using `sendto()`.
6. Close the socket.
7. Stop the program.

**Client Side:**

1. Start the program.
2. Create a UDP socket.
3. Send data to the server using `sendto()`.
4. Receive the server's response using `recvfrom()`.
5. Display the received message.
6. Close the socket.
7. Stop the program.

## Procedure for Executing the Python Program

* Open a Python programming environment such as IDLE, VS Code, PyCharm, or Google Colab.
* Create separate Python files for the TCP Server, TCP Client, UDP Server, and UDP Client.
* Import Python's `socket` module.
* For TCP communication, create a stream socket using `SOCK_STREAM`.
* For UDP communication, create a datagram socket using `SOCK_DGRAM`.
* Bind the server socket to the specified IP address and port number.
* Run the appropriate server program first and wait for client communication.
* Run the corresponding client program.
* Send a message from the client to the server.
* Receive and display the response from the server.
* Close the socket after communication is completed.
* Observe the messages displayed on both the client and server sides.

## Program

### TCP Program

#### Server

```python
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server.bind(("localhost", 5000))
server.listen(1)

print("Waiting for connection...")

conn, addr = server.accept()

print("Connected:", addr)

data = conn.recv(1024).decode()
print("Client:", data)

conn.send("Hello from TCP Server".encode())

conn.close()
server.close()
```

#### Client

```python
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(("localhost", 5000))

client.send("Hello from TCP Client".encode())

data = client.recv(1024).decode()

print("Server:", data)

client.close()
```

### UDP Program

#### Server

```python
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

server.bind(("localhost", 5001))

print("Waiting for message...")

data, addr = server.recvfrom(1024)

print("Client:", data.decode())

server.sendto("Hello from UDP Server".encode(), addr)

server.close()
```

#### Client

```python
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

client.sendto(
    "Hello from UDP Client".encode(),
    ("localhost", 5001)
)

data, addr = client.recvfrom(1024)

print("Server:", data.decode())

client.close()
```

## Output

### TCP Server

<img width="642" height="133" alt="image" src="https://github.com/user-attachments/assets/46e14ce7-a3db-498d-b566-1e330a5c5e7e" />

### TCP Client

<img width="631" height="62" alt="image" src="https://github.com/user-attachments/assets/3b755036-8bee-48da-917a-a0cc2b7e3cd9" />

### UDP Server

<img width="631" height="91" alt="image" src="https://github.com/user-attachments/assets/d7682725-f087-43ae-bd40-f0a96fcea734" />

### UDP Client

<img width="632" height="61" alt="image" src="https://github.com/user-attachments/assets/0b036fd5-b844-4350-bcb3-d0c6b35e9c5a" />


## Result

Thus, socket programming using TCP and UDP protocols was successfully implemented, and communication between the client and server was established successfully.
