<template>
  <div class="conversation">
    <h2>聊天对话框</h2>
    <div v-if="selectedChat">
      <p v-for="(message, index) in selectedChat.messages" :key="index">{{ message.text }}</p>
      <form @submit.prevent="sendMessage">
        <input v-model="newMessage" type="text" placeholder="请输入消息" />
        <button type="submit">发送</button>
      </form>
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  props: {
    selectedChat: {
      type: Object,
      required: true,
    },
  },
  emits: ["send-message"],
  setup(props, { emit }) {
    const newMessage = ref("");

    const sendMessage = () => {
      if (!newMessage.value) {
        return;
      }
      emit("send-message", newMessage.value);
      newMessage.value = "";
    };

    return {
      newMessage,
      sendMessage,
    };
  },
});
</script>

<style>
.conversation {
  flex: 5;
  background-color: #fff;
  padding: 1rem;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  overflow-y: scroll;
}

.conversation::-webkit-scrollbar {
  width: 5px;
  height: 5px;
}

.conversation::-webkit-scrollbar-thumb {
  background-color: #ccc;
  border-radius: 5px;
}

.conversation::-webkit-scrollbar-track {
  background-color: #f5f5f5;
  border-radius: 5px;
}

.conversation h2 {
  margin-top: 0;
  margin-bottom: 1rem;
}

.conversation p {
  margin-top: 0.5rem;
  padding: 0.5rem;
  border-radius: 5px;
  background-color: #e8f0fe;
  max-width: 80%;
}

.conversation form {
  margin-top: 1rem;
  display: flex;
  align-items: center;
}

.conversation input[type="text"] {
  flex: 1;
  padding: 0.5rem;
  border: none;
  border-radius: 5px;
  background-color: #f5f5f5;
}

.conversation button[type="submit"] {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 5px;
  background-color: #0088cc;
  color: #fff;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.conversation button[type="submit"]:hover {
  background-color: #006699;
}
</style>
