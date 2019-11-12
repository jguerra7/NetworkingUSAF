Moving on to the practical
First, we will make a server-side program that offers a connection to the client and sends a message to the client. Run server1.py:

import socket
host = "192.168.0.1" #Server address
port = 12345  #Port of Server
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((host,port)) #bind server 
s.listen(2) 
conn, addr = s.accept()  
print addr, "Now Connected"
conn.send("Thank you for connecting")
conn.close()
The preceding code is very simple; it is minimal code on the server side.

First, import the socket module and define the host and port number: 192.168.0.1 is the server's IP address. Socket.AF_INET defines the IPv4 protocol's family. Socket.SOCK_STREAM defines the TCP connection. The s.bind((host,port)) statement takes only one argument. It binds the socket to the host and port number. The s.listen(2) statement listens to the connection and waits for the client. The conn, addr = s.accept() statement returns two values: conn and addr. The conn socket is the client socket, as we discussed earlier. The conn.send() function sends the message to the client. Finally, conn.close() closes the socket. From the following examples and screenshot, you will understand conn better.

This is the output of the server1.py program:

G:\Python\Networking>python server1.py
Now, the server is in the listening mode and is waiting for the client:

Let's see the client-side code. Run client1.py:

import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = "192.168.0.1"  # server address
port =12345  #server port 
s.connect((host,port)) 
print s.recv(1024)
s.send("Hello Server")
s.close()
In the preceding code, two methods are new: s.connect((host,port)), which connects the client to the server, and s.recv(1024), which receives the strings sent by the server.

The output of client.py and the response of the server is shown in the following screenshot:
