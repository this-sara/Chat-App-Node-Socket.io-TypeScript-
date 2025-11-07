
# Chat App API

** Chat App** is a lightweight real-time chat application backend built with Node.js, Socket.io, and TypeScript. It supports multiple users, real-time messaging, and optional message history storage. The project focuses on type-safe socket events, modular classes for chat management, and a terminal or web client interface.

This README reflects the current features implemented in the repository.

---

## **Key Features**

* Multiple users can connect and chat simultaneously.
* Real-time messaging using Socket.io.
* Optional message history storage (in-memory or persistent).
* TypeScript interfaces for `Message` and `User` to ensure type safety.
* Chat management using modular classes.
* Terminal or web client support for sending and receiving messages.

---

## **Tech Stack**

* **Node.js (ES Modules)** – Server runtime
* **TypeScript** – Static typing for safer development
* **Socket.io** – Real-time bidirectional communication
* **Optional Database** – MongoDB, SQLite, or JSON storage for chat history
* **nodemon / ts-node** – Development tools for auto-reload and TypeScript execution

---

## **Quick Start**

### **1. Clone the repository and install dependencies**

```bash
git clone https://github.com/your-username/simple-chat-app.git
cd simple-chat-app
npm install
```

### **2. Create a `.env` file** at the project root (if you implement persistent storage)

Example variables:

```env
PORT=3000
CHAT_HISTORY_FILE=./data/messages.json
```

### **3. Start the dev server**

```bash
npm run dev
```

> The server will start at `http://localhost:3000` by default.

---

## **Important Routes and Features**

### **Socket Events**

* `connection` – When a user connects
* `message` – Send/receive chat messages
* `disconnect` – When a user disconnects

### **API / Web (optional terminal client)**

* `GET /` – Home or welcome page
* `POST /message` – Send a chat message (if REST endpoint implemented)
* `GET /messages` – List message history (optional)

---

## **Notes About Message Storage**

* Messages can be stored **in-memory** for real-time only, or optionally in a JSON file or database for persistence.
* The `ChatManager` class handles user sessions, message broadcasting, and optional storage.
* The terminal client sends messages via socket events; the web client can use a simple UI with HTML + JS.

---

## **Security and Validation**

* Currently no authentication is enforced, but type-safe events prevent invalid payloads.
* If implementing persistence, you may add **user authentication** or **JWT token validation**.

---

## **Project Structure (High Level)**

```
src/
  server.ts              # App entry point
  client.ts              # Terminal or web client
  chatManager.ts         # Chat management class
  types/
    Message.ts           # Message interface
    User.ts              # User interface
  utils/                 # Optional helpers (e.g., for storage)
```

---

## **Development Notes & Tips**

* TypeScript compilation and auto-reload:

```bash
npx tsc --watch
npm run dev
```

* Modular design with `ChatManager` allows adding features like private rooms, user authentication, or persistent storage.
* You can extend the project by connecting a MongoDB or SQLite database for messages.

---

## **Next Enhancements You Might Want**

* User authentication (JWT or session-based)
* Persistent message storage in MongoDB or SQLite
* Message editing/deletion
* Private chat rooms or group channels
* Web UI with React or EJS + Tailwind
* Unit and integration tests for socket events and classes
