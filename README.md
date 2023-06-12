# IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
# EXP: 3
# DATE:22-03-2023
# AIM :
To write a python program to perform sliding window protocol
# ALGORITHM :
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client otherwise it will sendNACK signal to client.
6. Stop the program
# CLIENT PROGRAM :

## Developed : ISHAQ HUSSAIN A
## Reg no : 212221040059

import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send:"))
l=list(range(size))
s=int(input("Enter Window Size:"))
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
# SERVER PROGRAM :
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
	print(s.recv(1024).decode())
	s.send("acknowledgement recieved from the server".encode())
```
# SERVER OUTPUT :
![241174922-6843d7a2-aa4b-449e-8c00-30a4a95672ae](https://github.com/ShakthiSundar-K/EX-3/assets/128116143/8f750665-add2-4c40-b7fc-fcbaad6c6527)


# CLIENT OUTPUT :
![241175011-6c74257e-da99-4c20-8f89-3ba4de8e0d9e](https://github.com/ShakthiSundar-K/EX-3/assets/128116143/91c9a285-26ef-4f14-a53d-e3b656c6ea3b)


# RESULT :
Thus, python program to perform stop and wait protocol was successfully executed.
