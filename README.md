# Simple TCP Server and Client in C++ with Winsock

This repository contains a simple implementation of a TCP server and client using C++ and the Winsock library. The server and client can exchange messages over a TCP connection.

## Prerequisites

Before running the code, ensure you have the following:

- C++ compiler
- Windows operating system (as Winsock is Windows-specific)
- Basic knowledge of C++ programming

## Server Setup

Follow these steps to set up the server:

1. **Initialize Winsock:** Open the server code (`SocketServer.cpp`) and locate the initialization section. This step loads the Winsock DLL and sets up necessary variables.

2. **Create a Socket:** Look for the section where the server socket is created. This involves specifying the address family, socket type, and protocol.

3. **Bind the Socket:** Find the code that binds the server socket to a specific IP address and port number.

4. **Listen for Connections:** Locate the code that puts the server socket in a state where it listens for incoming connections.

5. **Accept Connections:** Identify the code that accepts incoming connections and establishes a connection with a client.

6. **Receive and Send Data:** Look for the code that receives and sends data over the established TCP connection.

## Client Setup

Follow these steps to set up the client:

1. **Initialize Winsock and Create a Socket:** Open the client code (`SocketClient.cpp`) and find the section that initializes Winsock and creates a client socket.

2. **Connect to the Server:** Look for the code that connects the client to the server using the server's IP address and port number.

3. **Send and Receive Data:** Identify the code responsible for sending and receiving data in the client.

## How to Run

1. **Compile the Code:** Compile both the server and client codes using a C++ compiler. 
  cmd command: 1. g++ -o SocketServer SocketServer.cpp -lws2_32
               2. SocketServer.exe (SocketClient for client)

2. **Run the Server:** Execute the server executable in one terminal.

3. **Run the Client:** Execute the client executable in another terminal.

4. **Exchange Messages:** Follow the prompts to send and receive messages between the server and client.

## Additional Notes

- The server and client communicate over TCP on the loopback address (127.0.0.1) and port 55555. You can modify the IP address and port as needed.
- This code is a basic example and may not handle all edge cases or errors. Consider it as a starting point for more robust networked applications.


