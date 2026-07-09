<script setup lang="ts">
import { ref } from 'vue'
interface Contact { name: string; lastMessage: string; date: string; active: boolean }
interface Msg { from: string; date: string; message: string }
const contacts: Contact[] = [
  { name: 'Alice', lastMessage: 'See you in Our World!', date: 'Today', active: true },
  { name: 'Bob', lastMessage: 'Quest complete!', date: 'Yesterday', active: false },
]
const messages: Msg[] = [
  { from: 'Alice', date: '10:00 am', message: 'Hey! Are you joining the quest later?' },
  { from: 'me', date: '10:02 am', message: 'Yes! Just finishing up some karma votes.' },
  { from: 'Alice', date: '10:05 am', message: 'Great, see you in Our World!' },
]
const draft = ref('')
const emit = defineEmits<{ close: [] }>()
</script>
<template>
  <div class="msg-shell">
    <div class="msg-sidebar">
      <div class="msg-sidebar-title">Messages</div>
      <div v-for="c in contacts" :key="c.name" class="msg-contact" :class="{ 'msg-contact--active': c.active }">
        <div class="msg-contact-avatar">{{ c.name[0] }}</div>
        <div class="msg-contact-info">
          <span class="msg-contact-name">{{ c.name }}</span>
          <span class="msg-contact-last">{{ c.lastMessage }}</span>
        </div>
        <span class="msg-contact-date">{{ c.date }}</span>
      </div>
    </div>
    <div class="msg-main">
      <div class="msg-header">
        <span class="msg-header-name">Alice</span>
        <button class="msg-close-btn" @click="emit('close')">✕</button>
      </div>
      <div class="msg-feed">
        <div v-for="(m, i) in messages" :key="i" class="msg-bubble" :class="m.from === 'me' ? 'msg-bubble--me' : 'msg-bubble--them'">
          <span class="msg-text">{{ m.message }}</span>
          <span class="msg-date">{{ m.date }}</span>
        </div>
      </div>
      <form class="msg-compose" @submit.prevent="draft = ''">
        <input class="msg-input" v-model="draft" placeholder="Type a message..." />
        <button class="msg-send-btn" type="submit">Send</button>
      </form>
    </div>
  </div>
</template>
<style scoped>
.msg-shell{display:flex;height:420px;overflow:hidden;border-radius:12px}.msg-sidebar{width:200px;flex-shrink:0;border-right:1px solid rgba(0,200,255,.15);display:flex;flex-direction:column;overflow-y:auto}.msg-sidebar-title{font-family:'Orbitron',sans-serif;font-size:13px;color:#00c8ff;padding:16px 14px 10px;font-weight:700;letter-spacing:.06em}.msg-contact{display:flex;align-items:center;gap:10px;padding:10px 14px;cursor:pointer;transition:background .2s}.msg-contact:hover{background:rgba(0,200,255,.05)}.msg-contact--active{background:rgba(0,200,255,.08)}.msg-contact-avatar{width:34px;height:34px;border-radius:50%;background:linear-gradient(135deg,#00c8ff,#0080ff);display:flex;align-items:center;justify-content:center;font-family:'Orbitron',sans-serif;font-size:13px;color:#fff;font-weight:700;flex-shrink:0}.msg-contact-info{flex:1;overflow:hidden;display:flex;flex-direction:column;gap:2px}.msg-contact-name{font-size:13px;color:#fff;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}.msg-contact-last{font-size:11px;color:#7a9bbf;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}.msg-contact-date{font-size:10px;color:#5a7a9a;flex-shrink:0}.msg-main{flex:1;display:flex;flex-direction:column;overflow:hidden}.msg-header{display:flex;align-items:center;justify-content:space-between;padding:12px 16px;border-bottom:1px solid rgba(0,200,255,.12)}.msg-header-name{font-family:'Orbitron',sans-serif;font-size:14px;color:#fff;font-weight:700}.msg-close-btn{background:none;border:none;color:#7a9bbf;font-size:16px;cursor:pointer;padding:4px 8px}.msg-feed{flex:1;overflow-y:auto;padding:16px;display:flex;flex-direction:column;gap:10px}.msg-bubble{display:flex;flex-direction:column;gap:3px;max-width:75%}.msg-bubble--me{align-self:flex-end;align-items:flex-end}.msg-bubble--them{align-self:flex-start;align-items:flex-start}.msg-text{background:rgba(0,200,255,.12);border:1px solid rgba(0,200,255,.2);border-radius:10px;color:#fff;font-size:13px;padding:8px 12px;line-height:1.5}.msg-bubble--me .msg-text{background:rgba(0,128,255,.2);border-color:rgba(0,128,255,.3)}.msg-date{font-size:10px;color:#5a7a9a}.msg-compose{display:flex;gap:8px;padding:12px 16px;border-top:1px solid rgba(0,200,255,.12)}.msg-input{flex:1;background:rgba(255,255,255,.06);border:1px solid rgba(0,200,255,.2);border-radius:8px;color:#fff;font-size:13px;padding:9px 12px;outline:none;transition:border-color .2s}.msg-input:focus{border-color:rgba(0,200,255,.5)}.msg-send-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:11px;font-weight:700;letter-spacing:.06em;padding:9px 18px;cursor:pointer;transition:opacity .2s}.msg-send-btn:hover{opacity:.85}
</style>
