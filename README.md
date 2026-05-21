# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To write a python program to perform sliding window protocol 
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
DEVELOPED BY: THARANI RAMESHBABU     REG NO: 212225240170
client side:

import socket 
s = socket.socket() 
s.connect(('localhost',9000))
while True: 
    data = s.recv(1024).decode()
    if not data:
        break
    print(data) 
    s.send("acknowledgement received from the client".encode())

server side:

import socket 
s = socket.socket() 
s.bind(('localhost',9000)) 
s.listen(5) 
c,addr = s.accept() 
size = int(input("Enter number of frames to send : "))
l = list(range(size)) 
w = int(input("Enter Window Size : "))   
st = 0 
i = 0 
while True: 
    if(i < len(l)):   
        st = i + w    
        c.send(str(l[i:st]).encode()) 
        ack = c.recv(1024).decode() 
        if ack: 
            print(ack) 
            i += w 
    else:
        break
```
## OUPUT
<img width="1920" height="1080" alt="Screenshot (555)" src="https://github.com/user-attachments/assets/16a96ce0-d585-457c-91b5-973a1a24345f" />
<img width="1920" height="1080" alt="Screenshot (554)" src="https://github.com/user-attachments/assets/37ddea23-8942-48b5-a441-00c6f04ee1c0" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
