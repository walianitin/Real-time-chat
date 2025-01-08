# Real-Time Chat Application with Raw WebSockets                    
  

This project implements a real-time chat application using raw WebSockets in Node.js. It includes features for room management by admins and user participation, including sending messages, upvoting messages, and alerting admins for high-upvoted messages.

---

## Features

1. **Admin Functionalities**
   - Create a new chat room.
   - Set properties for the room:
     - `name`: Name of the chat room.
     - `start_time`: When the chat session starts.
     - `is_open`: Boolean to control if the room is open for new participants.
     - `cool_down_time`: Time in seconds to cool down the chat before ending.

2. **User Functionalities**
   - Join a chat room.
   - Send messages.
   - Upvote messages.

3. **Message Management**
   - Messages with more than 3 upvotes move to a "Highlighted" section.
   - Messages with more than 10 upvotes trigger an alert for the admin.

---

## Installation and Setup

1. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd chat-app
   ```

2. **Install Dependencies**
   ```bash
   npm install
   ```

3. **Run the Server**
   ```bash
   node server.js
   ```

4. **Access the Application**
   Open your browser and navigate to `http://localhost:3000`.

---

## API Endpoints

### WebSocket Events

#### Admin Events
- `create_room`
  - **Payload:** `{ name, start_time, is_open, cool_down_time }`
  - **Description:** Create a new room with the specified properties.

#### User Events
- `join_room`
  - **Payload:** `{ room_id, user_name }`
  - **Description:** Join an existing room by its ID.

- `send_message`
  - **Payload:** `{ room_id, user_name, message }`
  - **Description:** Send a chat message to the specified room.

- `upvote_message`
  - **Payload:** `{ room_id, message_id }`
  - **Description:** Upvote a message by its ID in the specified room.

#### Notification Events
- `highlighted_message`
  - **Payload:** `{ message_id, message }`
  - **Description:** Sent to notify all users when a message has 3+ upvotes.

- `admin_alert`
  - **Payload:** `{ message_id, message }`
  - **Description:** Sent to the admin when a message has 10+ upvotes.

---

## Folder Structure

```
chat-app/
├── server.js          # Main server file for WebSocket handling
├── public/            # Static files for the client
│   ├── index.html     # Main HTML file for the client
│   ├── app.js         # Client-side WebSocket handling
├── utils/             # Utility functions
│   └── roomManager.js # Manage room creation and operations
├── package.json       # Dependencies and project metadata
└── README.md          # Documentation
```

---

## Contributing

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature-name`.
3. Commit your changes: `git commit -m 'Add feature-name'`.
4. Push to the branch: `git push origin feature-name`.
5. Create a pull request.

---

## License

This project is licensed under the MIT License. See `LICENSE` for details.

---

## Acknowledgments

Special thanks to the WebSocket community and Node.js contributors for their incredible resources.
