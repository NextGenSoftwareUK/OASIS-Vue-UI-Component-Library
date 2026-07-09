<script setup lang="ts">
import { ref } from 'vue'
const emit = defineEmits<{ close: []; submit: [{ group: string; avatar: string; seedUser: string; amount: string; note: string }] }>()
const form = ref({ group: 'avatar', avatar: '', seedUser: '', amount: '', note: '' })
function handleSubmit() { emit('submit', { ...form.value }) }
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">✉️ Send Seeds Invite</h2>
    <form class="p-form" @submit.prevent="handleSubmit">
      <div class="p-row">
        <label class="p-label p-radio-label">
          <input type="radio" v-model="form.group" value="avatar" />
          Avatar
        </label>
        <input class="p-input" v-model="form.avatar" placeholder="Avatar username" :disabled="form.group !== 'avatar'" />
      </div>
      <div class="p-or">OR</div>
      <div class="p-row">
        <label class="p-label p-radio-label">
          <input type="radio" v-model="form.group" value="seedUser" />
          Seed Username
        </label>
        <input class="p-input" v-model="form.seedUser" placeholder="Seed Username" :disabled="form.group !== 'seedUser'" />
      </div>
      <div class="p-row"><label class="p-label">Amount</label><input class="p-input" v-model="form.amount" type="number" placeholder="Amount" :disabled="form.group !== 'seedUser'" /></div>
      <div class="p-row"><label class="p-label">Note</label><input class="p-input" v-model="form.note" placeholder="Optional message" /></div>
      <div class="p-actions"><button class="p-btn-cancel" type="button" @click="emit('close')">Cancel</button><button class="p-btn" type="submit">Send Invite</button></div>
    </form>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:16px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-form{display:flex;flex-direction:column;gap:12px}.p-row{display:flex;flex-direction:column;gap:6px}.p-label{font-size:12px;color:#7a9bbf;font-weight:600;letter-spacing:.05em}.p-radio-label{display:flex;align-items:center;gap:8px;font-size:13px;color:#c8dff0;cursor:pointer}.p-or{text-align:center;font-family:'Orbitron',sans-serif;font-size:11px;color:#5a7a9a;letter-spacing:.1em}.p-input{background:rgba(255,255,255,.06);border:1px solid rgba(0,200,255,.2);border-radius:8px;color:#fff;font-size:14px;padding:10px 12px;width:100%;box-sizing:border-box;outline:none;transition:border-color .2s}.p-input:focus{border-color:rgba(0,200,255,.5)}.p-input:disabled{opacity:.4;cursor:not-allowed}.p-actions{display:flex;gap:10px;justify-content:flex-end;margin-top:4px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}.p-btn-cancel{background:transparent;border:1px solid rgba(0,200,255,.3);border-radius:8px;color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer}
</style>
