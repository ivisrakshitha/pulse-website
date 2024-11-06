<template>
    <div>
      <!-- WhatsApp Button (fixed at the bottom-right) -->
      <div class="whatsapp-button">
        <img src="@/assets/whatsapp.png" alt="whatsapp" id="whatsapp" />
      </div>
  
      <!-- Chat Container (hidden by default) -->
      <div class="chat-container" id="chat-container">
        <div class="chat-header">
          <img src="@/assets/ivisdp.png" alt="Profile Picture" class="profile-picture" />
          <div class="chat-info">
            <span class="chat-name">PULSE</span>
            <span class="chat-status">Online</span>
          </div>
        </div>
        <div class="chat-messages" id="chat-messages">
          <div class="message received">
            Hello! We are excited to discuss your requirements for software solutions and digital transformation. Leave us a message, and we will get back to you promptly.
            <br /><br />
            Best regards, <br />
            PULSE
          </div>
        </div>
        <div class="chat-input">
          <input type="text" placeholder="Type a message" id="message-input" />
          <button id="sendButton">➤</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "WhatsApp",
    mounted() {
      const whatsapp = document.getElementById("whatsapp");
      const chatContainer = document.getElementById("chat-container");
      const messageInput = document.getElementById("message-input");
      const sendButton = document.getElementById("sendButton");
  
      const whatsappNumber = "+916364411444";
  
      chatContainer.style.display = "none"; // Hide the chat by default
      whatsapp.addEventListener("click", () => {
        // Toggle chat container visibility
        chatContainer.style.display = chatContainer.style.display === "none" ? "block" : "none";
      });
  
      function sendMessage() {
        const message = messageInput.value.trim();
        if (message) {
          const whatsappUrl = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(message)}`;
          window.open(whatsappUrl, "_blank");
          messageInput.value = ""; // Clear the input after sending
        }
      }
  
      sendButton.addEventListener("click", sendMessage);
  
      messageInput.addEventListener("keypress", (e) => {
        if (e.key === "Enter") {
          sendMessage();
        }
      });
    },
  };
  </script>
  
  <style scoped>
  .whatsapp-button {
    position: fixed;
    right: 4px; /* Ensure it's far from the edge */
    bottom: 20px; /* Place it slightly above the bottom */
    z-index: 10;
    cursor: pointer;
  }
  
  .whatsapp-button img {
    width: 50px;
    height: 50px;
  }
  
  .chat-container {
    width: 300px;
    position: fixed;
    right: 20px; /* Positioned to the right */
    bottom: 80px; /* Positioned above the WhatsApp button */
    border-radius: 1rem;
    z-index: 10;
    overflow: hidden;
    display: none;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
  }
  
  .chat-header {
    background-color: #075e54;
    color: white;
    padding: 10px;
    display: flex;
    align-items: center;
  }
  
  .profile-picture {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    margin-right: 10px;
    object-fit: cover;
  }
  
  .chat-info {
    display: flex;
    flex-direction: column;
  }
  
  .chat-name {
    font-weight: bold;
  }
  
  .chat-status {
    font-size: 0.8rem;
  }
  
  .chat-messages {
    padding: 10px;
    max-height: 300px;
    overflow-y: auto;
    background-color: #f1f1f1;
  }
  
  .message {
    padding: 10px;
    border-radius: 8px;
    margin-bottom: 10px;
    word-wrap: break-word;
  }
  
  .received {
    background-color: #dcf8c6;
  }
  
  .chat-input {
    padding: 10px;
    background-color: #ffffff;
    display: flex;
    align-items: center;
  }
  
  .chat-input input {
    flex-grow: 1;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 20px;
    margin-right: 10px;
  }
  
  .chat-input button {
    background-color: #075e54;
    color: white;
    border: none;
    padding: 10px;
    border-radius: 50%;
    cursor: pointer;
  }
  
  .chat-input button:hover {
    background-color: #128c7e;
  }
  </style>
  