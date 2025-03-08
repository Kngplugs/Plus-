HTML
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Clown Chat</title>
    <link rel="stylesheet" href="style.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">
</head>
<body>
    <div class="chat-app">
        <div class="chat-header">
            <h2>Clown Chat</h2>
            <button id="theme-toggle"><i class="fas fa-moon"></i></button>
        </div>
        <div class="chat-log" id="chat-log"></div>
        <div class="chat-input">
            <input type="text" id="message-input" placeholder="Type a message...">
            <button id="send-button">Send</button>
            <button id="emoji-button"><i class="fas fa-smile"></i></button>
            <button id="gif-button"><i class="fas fa-image"></i></button>
        </div>
        <div class="emoji-picker" id="emoji-picker">
            <!-- Emoji picker will be rendered here -->
        </div>
    </div>

    <script src="script.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/emoji-picker-element@1.2.2/dist/emoji-picker-element.min.js"></script>
</body>
</html>
```

CSS (in style.css file)
```
body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
}

.chat-app {
    width: 400px;
    height: 600px;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.chat-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #ccc;
}

.chat-header h2 {
    font-weight: bold;
    margin: 0;
}

.chat-header button {
    background-color: transparent;
    border: none;
    cursor: pointer;
}

.chat-log {
    height: 400px;
    overflow-y: auto;
    padding: 10px;
    border-bottom: 1px solid #ccc;
}

.chat-input {
    display: flex;
    align-items: center;
    padding: 10px;
}

#message-input {
    width: 70%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

#send-button {
    width: 15%;
    padding: 10px;
    background-color: #4CAF50;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

#send-button:hover {
    background-color: #3e8e41;
}

#emoji-button {
    width: 5%;
    padding: 10px;
    background-color: transparent;
    border: none;
    cursor: pointer;
}

#gif-button {
    width: 5%;
    padding: 10px;
    background-color: transparent;
    border: none;
    cursor: pointer;
}

.emoji-picker {
    position: absolute;
    top: 100%;
    left: 0;
    background-color: #fff;
    border: 1px solid #ccc;
    padding: 10px;
    display: none;
}

.emoji-picker.show {
    display: block;
}
```

JavaScript (in script.js file)
```
let messageInput = document.getElementById('message-input');
let sendButton = document.getElementById('send-button');
let chatLog = document.getElementById('chat-log');
let emojiButton = document.getElementById('emoji-button');
let gifButton = document.getElementById('gif-button');
let emojiPicker = document.getElementById('emoji-picker');
let themeToggle = document.getElementById('theme-toggle');

// Emoji picker
const emojiPickerElement = new EmojiPickerElement({
    rootElement: emojiPicker,
});
emojiPickerElement.addEventListener('emoji:select', (event) => {
    messageInput.value += event.detail.emoji;
});

// Theme toggle
themeToggle.addEventListener('click', () => {
    document.body.classList.toggle('dark-mode');
});

// Send button click event
sendButton.addEventListener('click', () => {
    let message = messageInput.value;
    if (message !== '') {
        let messageElement = document.createElement('div');
        messageElement.textContent = message;


```
        messageElement.textContent = message;
        chatLog.appendChild(messageElement);
        messageInput.value = '';
        chatLog.scrollTop = chatLog.scrollHeight;
    }
});

// Message input keypress event
messageInput.addEventListener('keypress', (event) => {
    if (event.key === 'Enter') {
        sendButton.click();
    }
});

// Emoji button click event
emojiButton.addEventListener('click', () => {
    emojiPicker.classList.toggle('show');
});

// Gif button click event
gifButton.addEventListener('click', () => {
    // Add GIF functionality here
});
```

```
