# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
To implement the sliding window protocol using python

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
 while(i<len(l)):
 st+=s
 c.send(str(l[i:st]).encode())
 ack=c.recv(1024).decode()
 if ack:
 print(ack)
 i+=s
```
### server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
REG NO:
while True:
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUTPUT
### client:
![image](https://github.com/arbasil05/2b_SLIDING_WINDOW_PROTOCOL/assets/144218037/46c626b8-f9e8-4916-8be7-82dda0fc9d90)
### server:
![image](https://github.com/arbasil05/2b_SLIDING_WINDOW_PROTOCOL/assets/144218037/fbc62fc9-99d4-4bfc-a26b-46199ea31afd)



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
