<script setup lang="ts">
import ChatMessages from '@/components/chat/ChatMessages.vue';
import MessageBox from '@/components/chat/MessageBox.vue';
import type { ChatMessage } from '@/interfaces/chat-message.interface';
import { ref } from 'vue';

const messages = ref<ChatMessage[]>([
  {
    id: new Date().getTime(),
    message: 'Hello',
    isMyMessage: true,
  },
  {
    id: new Date().getTime(),
    message: 'Do you want some coffee?',
    isMyMessage: true,
  },
  {
    id: new Date().getTime() + 1,
    message: 'No',
    isMyMessage: false,
    image: 'https://yesno.wtf/assets/no/2-101be1e3d8a0ed407c4e3c001ef8fa66.gif'
  },
]);

const onMessage = ( text: string ) => {
  messages.value.push({
    id: new Date().getTime() ,
    isMyMessage: true,
    message: text
  });
}
</script>

<!-- Fuente: https://tailwindcomponents.com/component/chat-layout -->
<template>
  <div class="bg-gray-100 h-screen flex flex-col max-w-lg mx-auto">
    <div class="bg-blue-500 p-4 text-white flex justify-between items-center">
      <span>Chatbot</span>
    </div>

    <ChatMessages :messages="messages" />

    <MessageBox @send-message="onMessage($event)" />
  </div>
</template>
