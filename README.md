# Chat App

This project is a real-time chat application built using the MERN stack (MongoDB, Express.js, React.js, Node.js). The application supports user authentication, real-time messaging with Socket.io, and integration with a language model API for automated responses.

## Table of Contents
- [Setup and Run Instructions](#setup-and-run-instructions)
- [API Route Descriptions](#api-route-descriptions)
- [Environment Configurations](#environment-configurations)

## Setup and Run Instructions

### Prerequisites
- Node.js
- MongoDB

### Backend Setup
1. Clone the repository:
   ```sh
   git clone https://github.com/your-repo/chat-app.git
   cd chat-app

Install server dependencies:
npm install
Create a .env file in the root directory and add the following:
MONGO_URI=mongodb://localhost:27017/chat-app
JWT_SECRET=your_jwt_secret
LLM_API_URL=https://api.example.com/llm
LLM_API_TIMEOUT=10000
Start the backend server:
npm run server

Frontend Setup
Navigate to the client directory:
cd client
Install client dependencies:
npm install
Start the frontend development server:
npm start
Open your browser and navigate to http://localhost:3000.

API Route Descriptions
User Authentication
Register
URL: /api/auth/register
Method: POST
Description: Register a new user.
{
  "email": "user@example.com",
  "password": "password123"
}

Expected Output:
201: User registered
400: Error registering user
Login
URL: /api/auth/login
Method: POST
Description: Log in a user.
{
  "email": "user@example.com",
  "password": "password123"
}
{
  "token": "jwt_token"
}
400: Invalid email or password

User Status
Set Status
URL: /api/status
Method: POST
Description: Set user status (AVAILABLE or BUSY).
{
  "status": "AVAILABLE" // or "BUSY"
}
Expected Output:
200: Status updated
400: Error updating status

Real-time Messaging
Join Chat
Event: join
Description: Join a chat room.
{
  "userId": "user_id"
}
Set Status
Event: setStatus
Description: Set user status.
{
  "userId": "user_id",
  "status": "AVAILABLE" // or "BUSY"
}
Send Message
Event: sendMessage
Description: Send a message to a recipient.
{
  "senderId": "user_id",
  "recipientId": "recipient_id",
  "message": "Hello!"
}
Get Messages
Event: getMessages
Description: Retrieve message history between two users.
{
  "userId": "user_id",
  "recipientId": "recipient_id"
}
{
  "userId": "user_id",
  "recipientId": "recipient_id"
}

Logic Overview
User Registration: Creates a new user with a hashed password.
User Login: Authenticates a user and returns a JWT token.
Set Status: Updates the user's status (AVAILABLE or BUSY).
Real-time Messaging:
Users can join a chat room identified by their user ID.
Users can set their status.
If a user is BUSY, incoming messages will trigger a request to an LLM API for an automated response.
Messages are stored in MongoDB and can be retrieved for chat history.

Environment Configurations
Backend
MONGO_URI: The MongoDB connection string.
JWT_SECRET: The secret key for signing JWT tokens.
LLM_API_URL: The URL of the language model API.
LLM_API_TIMEOUT: The timeout for the language model API request in milliseconds.
Frontend
No specific environment configurations are required. The frontend connects to the backend running on http://localhost:5000 by default.
Running the Application
Ensure MongoDB is running on your local machine.
Start the backend server.
Start the frontend development server.
Open your browser and navigate to http://localhost:3000.
Register a new user, log in, and start chatting!

License
This project is licensed under the MIT License.

Feel free to copy and use this content for your `README.md` file.
