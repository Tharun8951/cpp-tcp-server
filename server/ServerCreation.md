Creating a socket server instance requires 7 steps:-
1. Initialize WSA - WSAStartup()  -- loading the dll, initialzing wsa viraibles 
2. Create socket - socket() -- creating a socket, choosing protocol i.e, TCP or UDP
3. Bind the socket - bind() -- binding ip address and port number to the socket
4. Listen on the socket - listen()
5. Accept a connection - accept(), connect()
6. Send and receive data - recv(), send(), recvfrom(), sendto()
7. Disconnect - closesocket()


**second step:-**
# 2. Initialize the socket
the socket function take 3 parameters-> **socket(af, type, protocol)**
    1. af: address family specification (AF_INET for TCP or UDP)
    2. type: the type specification for new socket (SOCK_STREAM for TCP and SOCK_DGRAM for UDP)
    3. protocol: the protocol to be used (IPPROTO_TCP for TCP)
    The function returns a int, if 0 the socket creation was success, non-zero mean failed


**third step:-**
# 3. Binding ip address and port number to the socket
the bind function takes 3 parameters-> **int bind(SOCKET serverSocker, const struct sockaddr* name, int socklen);**
    1. SOCKET serverSocket -> it takes the unbound socket we created in the second step
    2. name -> Addres to assign the socket from the sockaddr structure
    3. socklen -> length i n bytes of the address structure i.e, name
    The function returns 0, if bind was successfull. otherwise, it return SOCKET_ERROR

    The second parameter sockaddr structure ->
        The sockaddr_in structure in widely used in Windows Socket (IP4) to specify a local or remote endpoint address to which to connect a socket
            struct sockaddr_in{
                short sin_family;
                unsigned short sin_port;
                struct in_addr sin_addr;
                char sin_zero[8];
            }
        * sin_family -> Adress family (must be AF_INET) //refer 2nd step of ServerCreation for AF_INET details
        * sin_port -> IP port
        * sin_addr -> IP address
        * sin_zero -> Padding to make structure same size as SOCKADDR, htons function return the value in 
        TCP/IP network byte (big endian) order from host byte (little endian) order //for more info about byte order refer **https://www.ibm.com/docs/en/zvm/7.2?topic=domains-network-byte-order-host-byte-order**



**forth step:-**
# 4. Listen on the socket - listen()
Places a socket in a state where it is listening for a incoming connection. -> 
    **int listen(SOCKET serverSocket, int backlog)**
    1. serverSocket: is a bound and unconnected socket
    2. backlog: The maximum number of connections allowed, It is OS dependent
    If there is no error, listen returns zero. Otherwise, a value of SOCKET_ERROR is returned


**fifth step:-**
# 5. Accept a connection - accept()
* It permits an incomming connection on a socket
* This is a blocking function, it will block the execution of the server until client is accepted
   **SOCKET accept(SOCKET serverSocket, struct sockaddr* addr, int* addrlen)**
    1. serverSocket: Is a bound socket and is on state of listening
    2. addr: Optional structure containing client's address and information //structure used in step 3
    3. Optional size of the address structure
    If no error occurs, accept() returns a value of SOCKET, that is a descriptor for the new socket that is connected to the client. However, the original socker (serverSocker) will be still listening for new incomming connections


**sixth step:-**
The server will first receive the data and then send, but in client the process is opposite i.e, send data first then receive
# 6(a). receing data on a connected socket - recv()
   **int recv(SOCKER acceptSocket, char *buff, int len, int flags)**
   1. acceptSocket : Socket that has been established with the client
   2. buff : Buffer to store received data
   3. len : Length of buffer
   4. flags : Optional, set of flags that influence the behavior of this function. ex- no routing
   If no error occurs, recv() returns 0 and stores data in buffer. Otherwise non-zero is returened

# 6(b). Sending data on a connected socket - send()
   **int send(SOCKET accpetSocket, const char *buff, int len, int flags)**
    1. acceptSocket: The descriptor that identifies a connected socket
    2. buf: A pointer to a buffer to the data to be transmitted
    3. len: Buffer's length in bytes
    4. flags: Optional, set of flags that influence the behavior of this function. ex- no routing
    If no error occurs, send() returns the number of bytes sent. Otherwise, SOCKET_ERROR is returned



