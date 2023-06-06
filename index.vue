<template>
  <div class="container">
    <MerchantList :merchants="merchants" :select-merchant="selectMerchant" />
    <ChatList :selected-merchant="selectedMerchant" :select-chat="selectChat" />
    <Conversation :selected-chat="selectedChat" @send-message="sendMessage" />
  </div>
</template>

<script>

import {MerchantList, ChatList, Conversation} from "@/components/Telegram";
import { defineComponent, ref } from "vue";

export default defineComponent({
  components: {
    MerchantList,
    ChatList,
    Conversation,
  },
  setup() {
    const merchants = ref([
      {
        id: 1,
        name: "商户1",
        chats: [
          {
            user: "用户A",
            messages: [
              { text: "商户1，你好吗？" },
              { text: "我想问一下......" },
            ],
          },
          {
            user: "用户B",
            messages: [
              { text: "你好，商户1，我对你的产品非常感兴趣。" },
            ],
          },
        ],
      },
      {
        id: 2,
        name: "商户2",
        chats: [
          {
            user: "用户C",
            messages: [
              { text: "你好，商户2，我看中了你的服务，可以详谈一下吗？" },
            ],
          },
        ],
      },
    ]);

    const selectedMerchant = ref(null);
    const selectedChat = ref(null);

    const selectMerchant = (merchant) => {
      selectedMerchant.value = merchant;
      selectedChat.value = null;
    };

    const selectChat = (chat) => {
      selectedChat.value = chat;
    };

    const sendMessage = (message) => {
      if (!message) {
        return;
      }
      selectedChat.value.messages.push({ text: message });
    };

    return {
      merchants,
      selectedMerchant,
      selectedChat,
      selectMerchant,
      selectChat,
      sendMessage,
    };
  },
});
</script>

<style>
.container {
  display: flex;
  justify-content: space-between;
  background-color: #f5f5f5;
  font-size: 1.3rem;
  height: 100vh;
  max-width: 100%;
}


</style>
