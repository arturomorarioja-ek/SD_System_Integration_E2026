### TCP/IP

1. Write a small TCP server and client in the programming language of your choice (Python, Java, C#, Go, Node.js recommended, in that order).

    - The server will open a random TCP port
    - The client will receive as parameters
       - A port number (that opened by the server)
       - A text message
    - The client will establish a connection with the server socket and send the message as a parameter
    - The server will echo the message back
    - The client will send the following information to the standard output:
       - Number of bytes sent
       - Number of bytes received
       - Text of the received message
    - Extra: calculate the time each request-response takes, including TCP connection establishment
  
2. Write a small UDP server and client similar to the TCP one. 
