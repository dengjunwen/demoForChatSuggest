<template>
  <div class="chats">
    <h2>聊天列表</h2>
    <ul v-if="selectedMerchant">
      <li class="chat-item" v-for="(chat, index) in selectedMerchant.chats" :key="index" @click="selectChat(chat)">
        {{ chat.user }}
      </li>
    </ul>
  </div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    selectedMerchant: {
      type: Object,
      required: true,
    },
    selectChat: {
      type: Function,
      required: true,
    },
  },
});
</script>

<style>
.chats {
  flex: 3;
  margin-right: 1rem;
  background-color: #fff;
  padding: 1rem;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.chat-item {
  display: flex;
  align-items: center;
  padding: 1rem;
  cursor: pointer;
  transition: background-color 0.2s ease;
  /*border-bottom: 1px solid #f5f5f5;*/
  border-radius: 1px;
  border-bottom: 1px solid #e3e0e0;
}

.chat-item:last-child {
  border-bottom: none;
}

.chat-item:hover {
  background-color: #f5f5f5;
}

.chat-item.active {
  background-color: #e8f0fe;
}

.chat-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  margin-right: 1rem;
  background-color: #e8e8e8;
}

.chat-info {
  flex: 1;
}

.chat-info h3 {
  margin-top: 0;
  margin-bottom: 0.5rem;
}

.chat-info p {
  margin: 0;
  font-size: 0.8rem;
  color: #888;
}
</style>
