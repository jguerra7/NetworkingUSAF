# General socket methods
The general socket methods are as follows:

* socket.recv(bufsize): This method receives a TCP message from the socket. The bufsize argument defines the maximum data it can receive at any one time.
* socket.recvfrom(bufsize): This method receives data from the socket. The method returns a pair of values: the first value gives the received data, and the second value gives the address of the socket sending the data.
* socket.recv_into(buffer): This method receives data less than or equal to buffer. The buffer parameter is created by the bytearray() method. We will discuss it in an example later.
* socket.recvfrom_into(buffer): This method obtains data from the socket and writes it into the buffer. The return value is a pair (nbytes, address), where nbytes is the number of bytes received, and the address is the address of the socket sending the data.
