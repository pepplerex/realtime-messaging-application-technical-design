# Real-time Messaging System Technical Documentation 

 

# Presented by: Rex Pepple 

 

# System Architecture Overview 

In this document, I will outline the technical architecture and design decisions for my real-time messaging system. This system is built using a modern technology which include Node.js for the server logic, socket.io as bridge for the real-time communication, Redis for caching and TypeScript for type safety across the entire application. 

 

I'm keeping the architecture simple and with three main components: 

A single backend server handling both WebSocket connections and HTTP requests 

A primary database for message storage (MySQL) 

Redis for handling real-time features and caching 

 
![image-removebg-preview (1)](https://github.com/user-attachments/assets/81544793-0325-4eed-8fd1-426adfcc2393)
 
 

# Database schema 

 
![image-removebg-preview (2)](https://github.com/user-attachments/assets/dddccaae-6763-4736-aafb-8eb5782ae1b9)
 

 

 

 

 

 

 

  

# Real-Time Implementation 

  

The real-time chat system is  built using Socket.io and Node.js. 

 

# Here’s How It Works 

  

When someone wants to chat, Socket.io client first says hi to my Node.js server with their auth token. then we check in with Redis to keep track of who's who in a session. Once Redis gives the thumbs up, we're good to go! 

  

To join a chat, Socket.io client sends a "join" event, and the Node.js server works with Redis to add them to the right channel. 

  

For messaging, Socket.io handles all the real-time bridge while the Node.js server communicates with the database and Redis to keep track of message states. 

  
![image-removebg-preview (3)](https://github.com/user-attachments/assets/ace97679-b6b5-4c89-b911-00195569ce41)
 

  

# Message States 

 

 ![image-removebg-preview (6)](https://github.com/user-attachments/assets/b746d7aa-9c19-438b-a5ed-7586a446aeb0)

 
# Message differentiation between roles 

 

The logic here is to emit back a message sent to the server with the role of the sending user. When this information/property is returned back, the frontend can easily pick this up and render the texts based on the role of the user sending. Below is a diagram to illustrate my idea 
  

 ![image-removebg-preview (7)](https://github.com/user-attachments/assets/7b8c1363-954d-4200-99e8-99e71b2c6be4)
 

# Scalability Approach 

 

I'm keeping the scaling strategy simple: 

- Redis for managing WebSocket sessions 

- Database indexing for faster queries 

  

# Error Handling 

Basic error handling covers: 

- Connection drops 

- Message delivery failures 

- Database transaction failures 

   

# Future Considerations 

Core improvements I'd consider: 

- Message search 

- File sharing (images) 

- Message reactions 
