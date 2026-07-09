<script setup lang="ts">
import { ref } from 'vue'
const emit = defineEmits<{ close: []; submit: [{ group: string; username: string; inviteSecret: string }] }>()
const form = ref({ group: 'avatar', username: '', inviteSecret: '' })
function handleSubmit() { emit('submit', { ...form.value }) }
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">🌱 Accept Invite to Join Seeds</h2>
    <form class="p-form" @submit.prevent="handleSubmit">
      <div class="p-row">
        <label class="p-label">Search by</label>
        <div class="p-radio-group">
          <label class="p-radio"><input type="radio" v-model="form.group" value="avatar" /> Avatar</label>
          <label class="p-radio"><input type="radio" v-model="form.group" value="seedUsername" /> Seed Username</label>
        </div>
      </div>
      <div class="p-row"><label class="p-label">{{ form.group === 'avatar' ? 'Avatar Username' : 'Seed Username' }}</label><input class="p-input" v-model="form.username" placeholder="username" /></div>
      <div class="p-row"><label class="p-label">Invite Secret</label><input class="p-input" v-model="form.inviteSecret" placeholder="Your invite secret code" /></div>
      <div class="p-actions"><button class="p-btn-cancel" type="button" @click="emit('close')">Cancel</button><button class="p-btn" type="submit">Accept Invitation</button></div>
    </form>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:20px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-form{display:flex;flex-direction:column;gap:14px}.p-row{display:flex;flex-direction:column;gap:6px}.p-label{font-size:12px;color:#7a9bbf;font-weight:600;letter-spacing:.05em}.p-radio-group{display:flex;gap:20px}.p-radio{display:flex;align-items:center;gap:6px;font-size:13px;color:#c8dff0;cursor:pointer}.p-input{background:rgba(255,255,255,.06);border:1px solid rgba(0,200,255,.2);border-radius:8px;color:#fff;font-size:14px;padding:10px 12px;width:100%;box-sizing:border-box;outline:none;transition:border-color .2s}.p-input:focus{border-color:rgba(0,200,255,.5)}.p-actions{display:flex;gap:10px;justify-content:flex-end;margin-top:4px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}.p-btn-cancel{background:transparent;border:1px solid rgba(0,200,255,.3);border-radius:8px;color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer}
</style>
