# sockets
#### just me doing random stuff with sockets ; ) (basically me learning sockets)

1) I learnt how to send objects. really simple xD 

- Server
```py
import socket
import struct

HEADERSIZE = 10

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((socket.gethostname(), 5050))
s.listen(5)
print("Server Started!")

while True:
    csocket, addr = s.accept()
    print(f"New connection: {addr}!")
    
    msg = struct.pack("i", 34)
    csocket.send(msg)
```

- Client
```py
import socket
import struct

HEADERSIZE = 10

IP = socket.gethostbyname(socket.gethostname())
PORT = 5050

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((IP, PORT))

msg = s.recv(1024)
print(struct.unpack("i", msg)[0])
```
