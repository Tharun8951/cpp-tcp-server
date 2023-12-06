creating a client requires 5 steps:-
1. Initialize WSA - WSAStartup()
2. Create a socker - socket()
3. Connect to the server - connect()
4. Send and receive data - send(), recv(), recvfrom(), sendto()
5. Disconnet - closesocket()

**refer Servercreation.md for 1 and 2 steps**

**third step**
## Step 3: Connecting to the server 
The connect function connects client to the server
within the client binding in performed automaticaly
    **int connect(SOCKET clientSocket, const sockaddr* addr, socklen_t addrlen)**
    1. ClientSocket:- the socket we created in the previos step
    2. Structure containing server ip and port number
    3. Size in bytes of the addr structure
    Connect will wait for 75 seconds for server to respond
    Returns 0 if successfull, SOCKET_ERROR if error

**forth step**
## step 4(a): and step 4(b) sending and receiving data, refer SocketCreation.md

