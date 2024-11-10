<template>
  <div class="container mt-5">
    <!-- Navbar Header -->
    <nav class="navbar navbar-expand-lg navbar-light bg-light mb-4">
      <a class="navbar-brand" href="#">IITM Student Project Tracker</a>
      <div class="collapse navbar-collapse">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item">
            <a class="nav-link" @click="goToDashboard">Dashboard</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" @click="goToMyTeam">My Team</a>
          </li>
          <li class="nav-item active">
            <a class="nav-link" @click="goToInbox">Inbox</a>
          </li>
        </ul>
        <button class="btn btn-outline-danger my-2 my-sm-0" @click="logout">Logout</button>
      </div>
    </nav>

    <!-- Chat Container -->
    <div class="container p-3 chat-container">
      <div class="chat-header d-flex justify-content-between align-items-center mb-3">
        <h4 class="m-0">Inbox Chat</h4>
        <button class="btn btn-primary" @click="startNewChat">Compose</button>
      </div>

      <!-- Chat messages area -->
      <div class="chat-box mb-3" ref="chatBox">
        <div v-for="message in messages" :key="message.timestamp" class="message-container">
          <div :class="{'message-sent': message.isMine, 'message-received': !message.isMine}">
            <p class="message-content">{{ message.content }}</p>
            <div class="message-info">
              <span class="message-from">{{ message.from }}</span>
              <span class="message-timestamp">{{ message.timestamp }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Message input area -->
      <div class="input-area d-flex">
        <input 
          type="text" 
          v-model="newMessage" 
          class="form-control me-2" 
          placeholder="Write a message..."
          @keyup.enter="sendMessage"
        />
        <button class="btn btn-success" @click="sendMessage">Send</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      messages: [
        { from: 'John Doe', content: 'Hello, how can I assist you?', timestamp: '10:00 AM', isMine: false },
        { from: 'Me', content: 'I wanted to discuss the project details.', timestamp: '10:05 AM', isMine: true },
        { from: 'John Doe', content: 'Sure, let’s go over it.', timestamp: '10:07 AM', isMine: false },
      ],
      newMessage: '',
    };
  },
  methods: {
    goToDashboard() {
      this.$router.push('/dashboard');
    },
    goToMyTeam() {
      this.$router.push('/dashboard/myteam');
    },
    goToInbox() {
      this.$router.push('/dashboard/inbox');
    },
    logout() {
      this.$router.push('/');
    },
    startNewChat() {
      alert('Start a new chat');
    },
    sendMessage() {
      if (this.newMessage.trim()) {
        this.messages.push({
          from: 'Me',
          content: this.newMessage,
          timestamp: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' }),
          isMine: true,
        });
        this.newMessage = '';
        this.scrollToBottom();
      }
    },
    scrollToBottom() {
      this.$nextTick(() => {
        this.$refs.chatBox.scrollTop = this.$refs.chatBox.scrollHeight;
      });
    },
  },
  mounted() {
    this.scrollToBottom();
  },
};
</script>

<style scoped>
.container {
  max-width: 600px;
  background-color: #f5f7fa;
  border-radius: 8px;
}

.navbar-brand {
  font-weight: bold;
}

.chat-container {
  background-color: #ffffff;
  border-radius: 8px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
}

.chat-header {
  font-weight: bold;
  color: #4a4a4a;
}

.chat-box {
  height: 400px;
  overflow-y: auto;
  padding: 15px;
  background-color: #ffffff;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
}

.message-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

.message-sent {
  align-self: flex-end;
  background-color: #dcf8c6;
  padding: 10px 15px;
  border-radius: 15px 15px 0 15px;
  max-width: 60%;
  color: #333;
}

.message-received {
  align-self: flex-start;
  background-color: #f1f1f1;
  padding: 10px 15px;
  border-radius: 15px 15px 15px 0;
  max-width: 60%;
  color: #333;
}

.message-content {
  margin: 0;
  font-size: 14px;
}

.message-info {
  font-size: 12px;
  color: #888;
  display: flex;
  justify-content: space-between;
}

.input-area {
  border-top: 1px solid #e0e0e0;
  padding-top: 10px;
}

.form-control {
  border-radius: 20px;
}

.btn-success {
  border-radius: 20px;
}
</style>
