# Real-Time Chat Application

A full-stack web application enabling real-time group communication using Spring Boot, WebSocket, and STOMP messaging. The application features a modern, dark-themed UI and provides instant message delivery with typing indicators.

### **Features**
* **Real-Time Messaging:** Instant message delivery to all connected clients via the /topic/messages broker.

* **Typing Indicators:** Broadcasts "User is typing..." status to other participants when activity is detected in the input field.

* **Dynamic UI:**  Responsive dark-mode interface.

   * Automated avatar generation based on username initials and persistent color hashing.

   * Message grouping to prevent redundant name displays for consecutive messages from the same sender.

* **WebSocket Fallback:** Integrated SockJS to ensure connectivity in browsers or networks that do not support raw WebSockets.
  
### **Project Structure**

```
src/main/java/com/chat/chatapp/
├── config/        # WebSocket and Message Broker configuration
├── controller/    # STOMP message mapping and routing logic
├── model/         # ChatMessage and Typing Status data models
└── ChatappApplication.java
```

### **Setup and Installation**

#### **Prerequisites**

   * Java Development Kit (JDK) 17 or higher

   *  Maven 3.6+

#### **Steps**

**1. Clone the repository:**

```
git clone https://github.com/varshithrevally/Real-Time-Chat-App.git
cd Real-Time-Chat-App
```

**2.Build the application:**

```
./mvnw clean install
```
**3.Run the application:**

```
./mvnw spring-boot:run
```
**4.Access the App:**

 Open http://localhost:8080 in your web browser.

### Message Handling Logic

The application uses two primary destinations for communication:

* **/app/sendMessage:** Receives messages from clients, which are then broadcasted to /topic/messages.


* **/app/typing:** Receives typing events and broadcasts them to /topic/typing with a 1.5-second timeout on the frontend to clear the status.

### Future Enhancements

* Implementation of private messaging (one-on-one).

* Database integration (PostgreSQL/MongoDB) for persistent chat history.

* User authentication via Spring Security and JWT.

* Support for file and image attachments