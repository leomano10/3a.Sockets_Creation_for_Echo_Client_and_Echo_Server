# 3a. CREATION OF ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS

**Name:** MANORAJAPRIYAN.L.E  
**Register Number:** 212225040227  
**Department:** B.E. CSE  
**College:** Saveetha Engineering College

## AIM

To write a Python program for creating Echo Client and Echo Server using TCP Sockets.

## ALGORITHM

1. Import the necessary modules in Python.
2. Create a socket connection using the socket module.
3. Start the server and wait for the client connection.
4. Send a message from the client to the server.
5. Receive the message from the client using the `recv()` function.
6. Send the same message back to the client using the `send()` function.
7. Display the echoed message on the client side.
8. Close the socket connection.

## PROGRAM

### 1. Echo Server Program

**File: `echo_server.py`**

```python
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'
port = 5000

server_socket.bind((host, port))
server_socket.listen(1)

print("Echo Server is waiting for connection...")

client_socket, addr = server_socket.accept()
print("Connected to:", addr)

while True:
    data = client_socket.recv(1024).decode()

    if not data:
        break

    print("Client:", data)
    client_socket.send(data.encode())

client_socket.close()
server_socket.close()
```

### 2. Echo Client Program

**File: `echo_client.py`**

```python
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'
port = 5000

client_socket.connect((host, port))

while True:
    message = input("Enter message: ")

    client_socket.send(message.encode())

    if message.lower() == 'exit':
        break

    data = client_socket.recv(1024).decode()
    print("Server echoed:", data)

client_socket.close()
```

## OUTPUT

### Server Side and Client Side Execution

![Echo Client and Echo Server Output](https://github.com/user-attachments/assets/0e8d9222-2429-4ce0-a5e5-f89a078a1f3b)

### Sample Output

**Server Side:**
```text
Echo Server is waiting for connection...
Connected to: ('127.0.0.1', 54321)
Client: hi
Client: i am mano
Client: what is your name
```

**Client Side:**
```text
Enter message: hi
Server echoed: hi

Enter message: i am mano
Server echoed: i am mano

Enter message: what is your name
Server echoed: what is your name
```

## HOW TO EXECUTE

1. Save the server program as `echo_server.py`.
2. Save the client program as `echo_client.py`.
3. Open the VS Code terminal.
4. Run the server first:

```bash
python echo_server.py
```

5. Open another terminal and run the client:

```bash
python echo_client.py
```

6. Enter messages in the client terminal and view the echoed messages.

## RESULT

Thus, the Python program for creating Echo Client and Echo Server using TCP Sockets was successfully created and executed.
