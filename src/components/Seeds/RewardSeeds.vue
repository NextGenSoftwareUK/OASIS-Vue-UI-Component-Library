<script setup lang="ts">
import { ref } from 'vue'
const emit = defineEmits<{ close: []; submit: [{ avatar: string; amount: number; reason: string }] }>()
const form = ref({ avatar: '', amount: 0, reason: '' })
function handleSubmit() { emit('submit', { ...form.value }) }
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">🏆 Reward Seeds</h2>
    <form class="p-form" @submit.prevent="handleSubmit">
      <div class="p-row"><label class="p-label">Avatar to Reward</label><input class="p-input" v-model="form.avatar" placeholder="Avatar username" /></div>
      <div class="p-row"><label class="p-label">Amount of SEEDS</label><input class="p-input" v-model.number="form.amount" type="number" placeholder="0" /></div>
      <div class="p-row"><label class="p-label">Reason</label><textarea class="p-textarea" v-model="form.reason" placeholder="Why are you rewarding this avatar?"></textarea></div>
      <div class="p-actions"><button class="p-btn-cancel" type="button" @click="emit('close')">Cancel</button><button class="p-btn" type="submit">Reward</button></div>
    </form>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:20px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-form{display:flex;flex-direction:column;gap:14px}.p-row{display:flex;flex-direction:column;gap:6px}.p-label{font-size:12px;color:#7a9bbf;font-weight:600;letter-spacing:.05em}.p-input,.p-textarea{background:rgba(255,255,255,.06);border:1px solid rgba(0,200,255,.2);border-radius:8px;color:#fff;font-size:14px;padding:10px 12px;width:100%;box-sizing:border-box;outline:none;transition:border-color .2s}.p-input:focus,.p-textarea:focus{border-color:rgba(0,200,255,.5)}.p-textarea{min-height:80px;resize:vertical}.p-actions{display:flex;gap:10px;justify-content:flex-end;margin-top:4px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}.p-btn-cancel{background:transparent;border:1px solid rgba(0,200,255,.3);border-radius:8px;color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer}
</style>
